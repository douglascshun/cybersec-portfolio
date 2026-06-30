<!-- ══════════════════════ IDIOMAS / LANGUAGES ══════════════════════ -->
<div align="center">
<a href="README.md"><img src="https://img.shields.io/badge/Portugu%C3%AAs-1987F0?style=for-the-badge" alt="Português"/></a>
<a href="README.en.md"><img src="https://img.shields.io/badge/English-555555?style=for-the-badge" alt="English"/></a>
<a href="README.es.md"><img src="https://img.shields.io/badge/Espa%C3%B1ol-555555?style=for-the-badge" alt="Español"/></a>
</div>

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

<!-- Cabeçalho animado -->
<div align="center">
  <a href="https://github.com/douglascshun/cybersec-portfolio">
    <img src="https://readme-typing-svg.demolab.com?font=VT323&size=30&duration=2600&pause=500&color=1987F0&center=true&vCenter=true&width=620&height=70&lines=Portfolio+de+Pentest;Ambientes+legais+e+autorizados;TryHackMe+%7C+HackTheBox+%7C+Labs+proprios;Da+exploracao+ao+relatorio+executivo" alt="Typing SVG"/>
  </a>
</div>

<h1 align="center">Cybersec Portfolio</h1>
<p align="center"><em>Evidência prática de testes de invasão conduzidos em ambientes legais e autorizados, do reconhecimento ao relatório executivo.</em></p>

<div align="center">

<img src="https://img.shields.io/badge/Pentest-RabbitSec_Red_Team-1987F0?style=for-the-badge&logo=hackthebox&logoColor=white" alt="pentest"/>
<img src="https://img.shields.io/badge/Metodologia-OSSTMM_%7C_OWASP-000000?style=for-the-badge" alt="metodologia"/>
<br/>
<img src="https://img.shields.io/github/stars/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=stars" alt="stars"/>
<img src="https://img.shields.io/github/forks/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=forks" alt="forks"/>
<img src="https://img.shields.io/github/last-commit/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=%C3%BAltimo%20commit" alt="last commit"/>
<img src="https://img.shields.io/github/license/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=licen%C3%A7a" alt="license"/>

</div>

<!-- ══════════════════════════ NAVEGAÇÃO ══════════════════════════ -->
<div align="center">

<a href="#sobre"><img src="https://img.shields.io/badge/SOBRE-1987F0?style=for-the-badge" alt="sobre"/></a>
<a href="#metodologia"><img src="https://img.shields.io/badge/METODOLOGIA-000000?style=for-the-badge" alt="metodologia"/></a>
<a href="#relatorios"><img src="https://img.shields.io/badge/RELAT%C3%93RIOS-1987F0?style=for-the-badge" alt="relatorios"/></a>
<a href="#skills"><img src="https://img.shields.io/badge/SKILLS-000000?style=for-the-badge" alt="skills"/></a>
<a href="#roadmap"><img src="https://img.shields.io/badge/ROADMAP-1987F0?style=for-the-badge" alt="roadmap"/></a>
<a href="#contato"><img src="https://img.shields.io/badge/CONTATO-000000?style=for-the-badge" alt="contato"/></a>

</div>

<br/>

<!-- ══════════════════════════ SOBRE ══════════════════════════ -->
<a id="sobre"></a>
## Sobre este portfólio

Sou Douglas Cshunderlick, analista de cibersegurança com foco em pentest, defesa de redes e análise de ameaças. Cada pasta deste repositório documenta um comprometimento real, executado em laboratório autorizado (TryHackMe, HackTheBox e ambientes próprios), com a mesma estrutura que eu entregaria a um cliente: prova de conceito, caminho de ataque passo a passo e recomendações priorizadas de correção.

A ideia não é só "capturar a flag". É mostrar como penso uma invasão de ponta a ponta e, principalmente, como traduzo o achado técnico em risco de negócio e em um plano de remediação que a equipe consegue executar.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ METODOLOGIA ══════════════════════════ -->
<a id="metodologia"></a>
## Como cada teste é conduzido

Todo relatório segue o mesmo fluxo, alinhado ao OSSTMM e ao OWASP Testing Guide. As cinco fases abaixo são clicáveis no índice e aparecem detalhadas em cada caso.

```mermaid
flowchart LR
    A[Reconhecimento] --> B[Enumeracao]
    B --> C[Exploracao]
    C --> D[Pos-exploracao<br/>e escalada]
    D --> E[Relatorio<br/>e remediacao]
    style A fill:#1987F0,stroke:#000,color:#fff
    style B fill:#000000,stroke:#1987F0,color:#fff
    style C fill:#1987F0,stroke:#000,color:#fff
    style D fill:#000000,stroke:#1987F0,color:#fff
    style E fill:#1987F0,stroke:#000,color:#fff
```

<div align="center">

| Fase | O que acontece |
|:--|:--|
| **Reconhecimento** | Mapeamento da superfície exposta, portas e serviços vivos |
| **Enumeração** | Investigação de cada serviço em busca de versão, configuração fraca e credencial |
| **Exploração** | Obtenção do primeiro acesso, com confirmação ativa da falha |
| **Pós-exploração** | Movimentação lateral e escalada até o controle total |
| **Relatório** | Tradução do achado em impacto de negócio e correção priorizada |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RELATÓRIOS ══════════════════════════ -->
<a id="relatorios"></a>
## Relatórios de teste de invasão

<div align="center">

| Máquina | Plataforma | Dificuldade | Tempo até root | Vetor principal | Status |
|:--|:--:|:--:|:--:|:--|:--:|
| **Poster** | TryHackMe | Média | ~1h40 | PostgreSQL com credencial padrão + `CVE-2019-9193` | Concluído |
| **Meow** | HackTheBox | Fácil | ~45min | Telnet com login de root direto (Alpine mal configurado) | Concluído |

</div>

Clique em cada caso para abrir o resumo do ataque sem sair desta página.

<details>
<summary><b>Poster · comprometimento total via PostgreSQL exposto</b></summary>

<br/>

> Banco PostgreSQL acessível pela rede com a senha de fábrica abriu a porta para execução de comandos no servidor. A partir daí, credenciais guardadas em texto puro e uma regra de `sudo` sem senha levaram ao acesso de root em menos de duas horas.

**Caminho resumido**

1. Varredura revelou a porta `5432` (PostgreSQL) aberta para a rede.
2. Login com a credencial padrão `postgres:password`.
3. Execução de comando no sistema explorando a `CVE-2019-9193` (função `COPY FROM PROGRAM`).
4. Leitura de arquivos de configuração com credenciais do usuário `dark` em texto puro.
5. Regra de `sudo` sem senha permitiu virar root.

**Por que importa:** três falhas isoladas e banais (senha de fábrica, segredo no código, `sudo` permissivo) encadeadas viram comprometimento crítico do servidor inteiro.

<div align="center">
<a href="/Relatorios/relatorioPosterTHM"><img src="https://img.shields.io/badge/Abrir_relat%C3%B3rio_completo-1987F0?style=for-the-badge&logo=tryhackme&logoColor=white" alt="poster"/></a>
</div>

</details>

<details>
<summary><b>Meow · acesso de root direto por Telnet</b></summary>

<br/>

> Um serviço Telnet exposto aceitava login de root sem qualquer barreira. Caso clássico de exposição de serviço legado que não deveria estar acessível.

**Caminho resumido**

1. Varredura revelou a porta `23` (Telnet) aberta.
2. Conexão direta e login como `root`, sem senha forte no caminho.
3. Controle total imediato da máquina.

**Por que importa:** serviços antigos em texto puro como Telnet não pertencem a nenhuma superfície moderna. A correção é desligar o serviço e bloquear a porta, não "colocar uma senha melhor".

<div align="center">
<a href="/Relatorios/relatorioMeowHTB"><img src="https://img.shields.io/badge/Abrir_relat%C3%B3rio_completo-1987F0?style=for-the-badge&logo=hackthebox&logoColor=white" alt="meow"/></a>
</div>

</details>

<br/>

<div align="center"><sub>Novos relatórios entram aqui conforme são concluídos.</sub></div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ SKILLS ══════════════════════════ -->
<a id="skills"></a>
## Competências demonstradas

<div align="center">

<img src="https://img.shields.io/badge/Nmap-4682B4?style=flat-square&logo=nmap&logoColor=white" alt="nmap"/>
<img src="https://img.shields.io/badge/Gobuster-00ADD8?style=flat-square&logo=go&logoColor=white" alt="gobuster"/>
<img src="https://img.shields.io/badge/ffuf-4B0082?style=flat-square" alt="ffuf"/>
<img src="https://img.shields.io/badge/Burp_Suite-FF6633?style=flat-square&logo=burpsuite&logoColor=white" alt="burp"/>
<img src="https://img.shields.io/badge/Metasploit-2596CD?style=flat-square&logo=metasploit&logoColor=white" alt="msf"/>
<img src="https://img.shields.io/badge/Linux_PrivEsc-FCC624?style=flat-square&logo=linux&logoColor=black" alt="privesc"/>

</div>

<table>
<tr>
<td valign="top" width="50%">

**Ofensiva**

- Reconhecimento e enumeração de serviços (Nmap, Gobuster, ffuf)
- Exploração de serviços expostos (PostgreSQL, SMB, HTTP, Telnet)
- Uso de credenciais padrão e segredos guardados em texto puro
- Escalada de privilégios em Linux (sudoers, SUID, capabilities)
- Exploração de CVEs conhecidas com prova de conceito

</td>
<td valign="top" width="50%">

**Consultiva**

- Documentação profissional de pentest (resumo executivo + técnico)
- Classificação de severidade e priorização de risco
- Recomendações de correção com prazo sugerido
- Tradução de achado técnico em impacto de negócio
- Alinhamento a OSSTMM e OWASP Testing Guide

</td>
</tr>
</table>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ROADMAP ══════════════════════════ -->
<a id="roadmap"></a>
## Próximos relatórios

- [ ] Web Application Pentest cobrindo o OWASP Top 10
- [ ] Comprometimento inicial em Active Directory
- [ ] Configurações inseguras em nuvem (AWS e Azure)
- [ ] Automação de reconhecimento com Python e Bash

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ CONTATO ══════════════════════════ -->
<a id="contato"></a>
## Contato

<div align="center">

<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="github"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="https://tryhackme.com/p/D.r4bbi7"><img src="https://img.shields.io/badge/TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="thm"/></a>
<a href="mailto:douglascshun@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email"/></a>

<br/><br/>

<em>Se o conteúdo te ajudou, uma estrela no repositório ajuda bastante. Obrigado pela visita.</em>

</div>

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center"><a href="#sobre"><img src="https://img.shields.io/badge/voltar_ao_topo-1987F0?style=flat-square" alt="topo"/></a></div>
