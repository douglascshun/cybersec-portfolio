<!-- ══════════════════════ IDIOMAS / LANGUAGES ══════════════════════ -->
<div align="center">
<a href="README.md"><img src="https://img.shields.io/badge/Portugu%C3%AAs-555555?style=for-the-badge" alt="Português"/></a>
<a href="README.en.md"><img src="https://img.shields.io/badge/English-555555?style=for-the-badge" alt="English"/></a>
<a href="README.es.md"><img src="https://img.shields.io/badge/Espa%C3%B1ol-1987F0?style=for-the-badge" alt="Español"/></a>
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
    <img src="https://readme-typing-svg.demolab.com?font=VT323&size=30&duration=2600&pause=500&color=1987F0&center=true&vCenter=true&width=620&height=70&lines=Portafolio+de+Pentest;Entornos+legales+y+autorizados;TryHackMe+%7C+HackTheBox+%7C+Labs+propios;De+la+explotacion+al+informe+ejecutivo" alt="Typing SVG"/>
  </a>
</div>

<h1 align="center">Cybersec Portfolio</h1>
<p align="center"><em>Evidencia práctica de pruebas de penetración realizadas en entornos legales y autorizados, del reconocimiento al informe ejecutivo.</em></p>

<div align="center">

<img src="https://img.shields.io/badge/Pentest-RabbitSec_Red_Team-1987F0?style=for-the-badge&logo=hackthebox&logoColor=white" alt="pentest"/>
<img src="https://img.shields.io/badge/Metodolog%C3%ADa-OSSTMM_%7C_OWASP-000000?style=for-the-badge" alt="metodologia"/>
<br/>
<img src="https://img.shields.io/github/stars/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=estrellas" alt="stars"/>
<img src="https://img.shields.io/github/forks/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=forks" alt="forks"/>
<img src="https://img.shields.io/github/last-commit/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=%C3%BAltimo%20commit" alt="last commit"/>
<img src="https://img.shields.io/github/license/douglascshun/cybersec-portfolio?style=flat-square&color=1987F0&label=licencia" alt="license"/>

</div>

<!-- ══════════════════════════ NAVEGAÇÃO ══════════════════════════ -->
<div align="center">

<a href="#sobre"><img src="https://img.shields.io/badge/ACERCA-1987F0?style=for-the-badge" alt="sobre"/></a>
<a href="#metodologia"><img src="https://img.shields.io/badge/METODOLOG%C3%8DA-000000?style=for-the-badge" alt="metodologia"/></a>
<a href="#relatorios"><img src="https://img.shields.io/badge/INFORMES-1987F0?style=for-the-badge" alt="relatorios"/></a>
<a href="#skills"><img src="https://img.shields.io/badge/SKILLS-000000?style=for-the-badge" alt="skills"/></a>
<a href="#roadmap"><img src="https://img.shields.io/badge/ROADMAP-1987F0?style=for-the-badge" alt="roadmap"/></a>
<a href="#contato"><img src="https://img.shields.io/badge/CONTACTO-000000?style=for-the-badge" alt="contato"/></a>

</div>

<br/>

<!-- ══════════════════════════ SOBRE ══════════════════════════ -->
<a id="sobre"></a>
## Sobre este portafolio

Soy Douglas Cshunderlick, analista de ciberseguridad enfocado en pentesting, defensa de redes y análisis de amenazas. Cada carpeta de este repositorio documenta un compromiso real, ejecutado en un laboratorio autorizado (TryHackMe, HackTheBox y entornos propios), con la misma estructura que entregaría a un cliente: prueba de concepto, ruta de ataque paso a paso y recomendaciones de corrección priorizadas.

La idea no es solo "capturar la flag". Es mostrar cómo razono una intrusión de principio a fin y, sobre todo, cómo traduzco el hallazgo técnico en riesgo de negocio y en un plan de remediación que el equipo puede ejecutar.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ METODOLOGIA ══════════════════════════ -->
<a id="metodologia"></a>
## Cómo se realiza cada prueba

Cada informe sigue el mismo flujo, alineado con el OSSTMM y la OWASP Testing Guide. Las cinco fases a continuación son clicables en el índice y aparecen detalladas en cada caso.

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

| Fase | Qué ocurre |
|:--|:--|
| **Reconocimiento** | Mapeo de la superficie expuesta, puertos y servicios activos |
| **Enumeración** | Investigación de cada servicio en busca de versión, configuración débil y credencial |
| **Explotación** | Obtención del primer acceso, con confirmación activa de la falla |
| **Post-explotación** | Movimiento lateral y escalada hasta el control total |
| **Informe** | Traducción del hallazgo en impacto de negocio y corrección priorizada |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RELATÓRIOS ══════════════════════════ -->
<a id="relatorios"></a>
## Informes de pruebas de penetración

<div align="center">

| Máquina | Plataforma | Dificultad | Tiempo hasta root | Vector principal | Estado |
|:--|:--:|:--:|:--:|:--|:--:|
| **Poster** | TryHackMe | Media | ~1h40 | PostgreSQL con credencial por defecto + `CVE-2019-9193` | Completado |
| **Meow** | HackTheBox | Fácil | ~45min | Telnet con login de root directo (Alpine mal configurado) | Completado |

</div>

Haz clic en cada caso para abrir el resumen del ataque sin salir de esta página.

<details>
<summary><b>Poster · compromiso total vía PostgreSQL expuesto</b></summary>

<br/>

> Una base de datos PostgreSQL accesible por la red con la contraseña de fábrica abrió la puerta a la ejecución de comandos en el servidor. A partir de ahí, credenciales guardadas en texto plano y una regla de `sudo` sin contraseña llevaron al acceso de root en menos de dos horas.

**Ruta resumida**

1. El escaneo reveló el puerto `5432` (PostgreSQL) abierto a la red.
2. Inicio de sesión con la credencial por defecto `postgres:password`.
3. Ejecución de comandos en el sistema explotando la `CVE-2019-9193` (función `COPY FROM PROGRAM`).
4. Lectura de archivos de configuración con las credenciales del usuario `dark` en texto plano.
5. Una regla de `sudo` sin contraseña permitió convertirse en root.

**Por qué importa:** tres fallas aisladas y triviales (contraseña de fábrica, secreto en el código, `sudo` permisivo) encadenadas se convierten en un compromiso crítico de todo el servidor.

<div align="center">
<a href="/Relatorios/relatorioPosterTHM"><img src="https://img.shields.io/badge/Abrir_informe_completo-1987F0?style=for-the-badge&logo=tryhackme&logoColor=white" alt="poster"/></a>
</div>

</details>

<details>
<summary><b>Meow · acceso de root directo por Telnet</b></summary>

<br/>

> Un servicio Telnet expuesto aceptaba login de root sin ninguna barrera. Caso clásico de exposición de un servicio heredado que no debería estar accesible.

**Ruta resumida**

1. El escaneo reveló el puerto `23` (Telnet) abierto.
2. Conexión directa e inicio de sesión como `root`, sin contraseña fuerte de por medio.
3. Control total inmediato de la máquina.

**Por qué importa:** los servicios antiguos en texto plano como Telnet no pertenecen a ninguna superficie moderna. La corrección es apagar el servicio y bloquear el puerto, no "poner una contraseña mejor".

<div align="center">
<a href="/Relatorios/relatorioMeowHTB"><img src="https://img.shields.io/badge/Abrir_informe_completo-1987F0?style=for-the-badge&logo=hackthebox&logoColor=white" alt="meow"/></a>
</div>

</details>

<br/>

<div align="center"><sub>Aquí se agregan nuevos informes a medida que se completan.</sub></div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ SKILLS ══════════════════════════ -->
<a id="skills"></a>
## Habilidades demostradas

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

- Reconocimiento y enumeración de servicios (Nmap, Gobuster, ffuf)
- Explotación de servicios expuestos (PostgreSQL, SMB, HTTP, Telnet)
- Uso de credenciales por defecto y secretos guardados en texto plano
- Escalada de privilegios en Linux (sudoers, SUID, capabilities)
- Explotación de CVEs conocidas con prueba de concepto

</td>
<td valign="top" width="50%">

**Consultiva**

- Documentación profesional de pentest (resumen ejecutivo + técnico)
- Clasificación de severidad y priorización de riesgo
- Recomendaciones de corrección con plazo sugerido
- Traducción del hallazgo técnico en impacto de negocio
- Alineación con OSSTMM y OWASP Testing Guide

</td>
</tr>
</table>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ROADMAP ══════════════════════════ -->
<a id="roadmap"></a>
## Próximos informes

- [ ] Web Application Pentest cubriendo el OWASP Top 10
- [ ] Compromiso inicial en Active Directory
- [ ] Configuraciones inseguras en la nube (AWS y Azure)
- [ ] Automatización de reconocimiento con Python y Bash

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ CONTATO ══════════════════════════ -->
<a id="contato"></a>
## Contacto

<div align="center">

<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="github"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="https://tryhackme.com/p/D.r4bbi7"><img src="https://img.shields.io/badge/TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="thm"/></a>
<a href="mailto:douglascshun@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email"/></a>

<br/><br/>

<em>Si este contenido te ayudó, una estrella en el repositorio ayuda mucho. Gracias por la visita.</em>

</div>

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center"><a href="#sobre"><img src="https://img.shields.io/badge/volver_arriba-1987F0?style=flat-square" alt="topo"/></a></div>
