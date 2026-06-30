<!-- ══════════════════════ IDIOMAS / LANGUAGES ══════════════════════ -->
<div align="center">
<a href="README.md"><img src="https://img.shields.io/badge/Portugu%C3%AAs-555555?style=for-the-badge" alt="Português"/></a>
<a href="README.en.md"><img src="https://img.shields.io/badge/English-1987F0?style=for-the-badge" alt="English"/></a>
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
    <img src="https://readme-typing-svg.demolab.com?font=VT323&size=30&duration=2600&pause=500&color=1987F0&center=true&vCenter=true&width=620&height=70&lines=Pentest+Portfolio;Legal+and+authorized+environments;TryHackMe+%7C+HackTheBox+%7C+Own+labs;From+exploitation+to+executive+report" alt="Typing SVG"/>
  </a>
</div>

<h1 align="center">Cybersec Portfolio</h1>
<p align="center"><em>Hands-on evidence of penetration tests conducted in legal and authorized environments, from reconnaissance to executive report.</em></p>

<div align="center">

<img src="https://img.shields.io/badge/Pentest-RabbitSec_Red_Team-1987F0?style=for-the-badge&logo=hackthebox&logoColor=white" alt="pentest"/>
<img src="https://img.shields.io/badge/Methodology-OSSTMM_%7C_OWASP-000000?style=for-the-badge" alt="metodologia"/>
<br/>
<img src="https://img.shields.io/github/stars/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=stars" alt="stars"/>
<img src="https://img.shields.io/github/forks/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=forks" alt="forks"/>
<img src="https://img.shields.io/github/last-commit/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=last%20commit" alt="last commit"/>
<img src="https://img.shields.io/github/license/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=license" alt="license"/>

</div>

<!-- ══════════════════════════ NAVEGAÇÃO ══════════════════════════ -->
<div align="center">

<a href="#sobre"><img src="https://img.shields.io/badge/ABOUT-1987F0?style=for-the-badge" alt="sobre"/></a>
<a href="#metodologia"><img src="https://img.shields.io/badge/METHODOLOGY-000000?style=for-the-badge" alt="metodologia"/></a>
<a href="#relatorios"><img src="https://img.shields.io/badge/REPORTS-1987F0?style=for-the-badge" alt="relatorios"/></a>
<a href="#skills"><img src="https://img.shields.io/badge/SKILLS-000000?style=for-the-badge" alt="skills"/></a>
<a href="#roadmap"><img src="https://img.shields.io/badge/ROADMAP-1987F0?style=for-the-badge" alt="roadmap"/></a>
<a href="#contato"><img src="https://img.shields.io/badge/CONTACT-000000?style=for-the-badge" alt="contato"/></a>

</div>

<br/>

<!-- ══════════════════════════ SOBRE ══════════════════════════ -->
<a id="sobre"></a>
## About this portfolio

I'm Douglas Cshunderlick, a cybersecurity analyst focused on pentesting, network defense, and threat analysis. Every folder in this repository documents a real compromise, carried out in an authorized lab (TryHackMe, HackTheBox, and my own environments), with the same structure I would deliver to a client: proof of concept, step-by-step attack path, and prioritized remediation recommendations.

The goal isn't just to "capture the flag." It's to show how I reason through an intrusion end to end and, above all, how I translate a technical finding into business risk and into a remediation plan the team can actually execute.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ METODOLOGIA ══════════════════════════ -->
<a id="metodologia"></a>
## How each test is conducted

Every report follows the same flow, aligned with the OSSTMM and the OWASP Testing Guide. The five phases below are clickable in the index and appear in detail in each case.

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

| Phase | What happens |
|:--|:--|
| **Reconnaissance** | Mapping the exposed surface, ports, and live services |
| **Enumeration** | Probing each service for version, weak configuration, and credentials |
| **Exploitation** | Gaining initial access, with active confirmation of the flaw |
| **Post-exploitation** | Lateral movement and escalation up to full control |
| **Reporting** | Translating the finding into business impact and prioritized remediation |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RELATÓRIOS ══════════════════════════ -->
<a id="relatorios"></a>
## Penetration test reports

<div align="center">

| Machine | Platform | Difficulty | Time to root | Main vector | Status |
|:--|:--:|:--:|:--:|:--|:--:|
| **Poster** | TryHackMe | Medium | ~1h40 | PostgreSQL with default credentials + `CVE-2019-9193` | Completed |
| **Meow** | HackTheBox | Easy | ~45min | Telnet with direct root login (misconfigured Alpine) | Completed |

</div>

Click each case to open the attack summary without leaving this page.

<details>
<summary><b>Poster · full compromise via exposed PostgreSQL</b></summary>

<br/>

> A PostgreSQL database reachable over the network with its factory password opened the door to command execution on the server. From there, credentials stored in plaintext and a passwordless `sudo` rule led to root access in under two hours.

**Path in brief**

1. A scan revealed port `5432` (PostgreSQL) open to the network.
2. Login with the default credential `postgres:password`.
3. System command execution by exploiting `CVE-2019-9193` (the `COPY FROM PROGRAM` function).
4. Reading configuration files holding the `dark` user's credentials in plaintext.
5. A passwordless `sudo` rule allowed becoming root.

**Why it matters:** three trivial standalone flaws (factory password, hardcoded secret, permissive `sudo`) chained together turn into a critical compromise of the entire server.

<div align="center">
<a href="/Relatorios/relatorioPosterTHM"><img src="https://img.shields.io/badge/Open_full_report-1987F0?style=for-the-badge&logo=tryhackme&logoColor=white" alt="poster"/></a>
</div>

</details>

<details>
<summary><b>Meow · direct root access over Telnet</b></summary>

<br/>

> An exposed Telnet service accepted root login without any barrier. A classic case of a legacy service left reachable when it should not be accessible at all.

**Path in brief**

1. A scan revealed port `23` (Telnet) open.
2. Direct connection and login as `root`, with no strong password in the way.
3. Immediate full control of the machine.

**Why it matters:** old plaintext services like Telnet have no place on any modern attack surface. The fix is to shut the service down and block the port, not to "set a better password."

<div align="center">
<a href="/Relatorios/relatorioMeowHTB"><img src="https://img.shields.io/badge/Open_full_report-1987F0?style=for-the-badge&logo=hackthebox&logoColor=white" alt="meow"/></a>
</div>

</details>

<br/>

<div align="center"><sub>New reports are added here as they are completed.</sub></div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ SKILLS ══════════════════════════ -->
<a id="skills"></a>
## Demonstrated skills

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

**Offensive**

- Service reconnaissance and enumeration (Nmap, Gobuster, ffuf)
- Exploitation of exposed services (PostgreSQL, SMB, HTTP, Telnet)
- Use of default credentials and secrets stored in plaintext
- Linux privilege escalation (sudoers, SUID, capabilities)
- Exploitation of known CVEs with proof of concept

</td>
<td valign="top" width="50%">

**Advisory**

- Professional pentest documentation (executive + technical summary)
- Severity rating and risk prioritization
- Remediation recommendations with a suggested deadline
- Translation of technical findings into business impact
- Alignment with OSSTMM and OWASP Testing Guide

</td>
</tr>
</table>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ROADMAP ══════════════════════════ -->
<a id="roadmap"></a>
## Upcoming reports

- [ ] Web application pentest covering the OWASP Top 10
- [ ] Initial compromise in Active Directory
- [ ] Insecure cloud configurations (AWS and Azure)
- [ ] Reconnaissance automation with Python and Bash

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ CONTATO ══════════════════════════ -->
<a id="contato"></a>
## Contact

<div align="center">

<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/GitHub_Profile-181717?style=for-the-badge&logo=github&logoColor=white" alt="github"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="https://tryhackme.com/p/D.r4bbi7"><img src="https://img.shields.io/badge/TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="thm"/></a>
<a href="mailto:douglascshun@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email"/></a>

<br/><br/>

<em>If this content helped you, a star on the repository goes a long way. Thanks for stopping by.</em>

</div>

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center"><a href="#sobre"><img src="https://img.shields.io/badge/back_to_top-1987F0?style=flat-square" alt="topo"/></a></div>
