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

<h1 align="center">Relatório de Pentest — Máquina "Meow"</h1>
<p align="center"><em>HackTheBox · RabbitSec Red Team</em></p>

<div align="center">

<img src="https://img.shields.io/badge/Plataforma-HackTheBox-9FEF00?style=for-the-badge&logo=hackthebox&logoColor=black" alt="htb"/>
<img src="https://img.shields.io/badge/Risco-CRÍTICO-d50000?style=for-the-badge" alt="risco"/>
<img src="https://img.shields.io/badge/CVSS-10.0-d50000?style=for-the-badge" alt="cvss"/>
<img src="https://img.shields.io/badge/Tempo_até_Root-~20min-1987F0?style=for-the-badge" alt="tempo"/>

</div>

<!-- ══════════════════════════ NAVEGAÇÃO ══════════════════════════ -->
<div align="center">

<a href="#resumo"><img src="https://img.shields.io/badge/▸_RESUMO-1987F0?style=for-the-badge" alt="resumo"/></a>
<a href="#falhas"><img src="https://img.shields.io/badge/▸_FALHAS-000000?style=for-the-badge" alt="falhas"/></a>
<a href="#relatorio"><img src="https://img.shields.io/badge/▸_RELATÓRIO_COMPLETO-1987F0?style=for-the-badge" alt="pdf"/></a>

</div>

<br/>

<div align="center">

| Classificação | Data do Teste | Metodologia | Resultado |
|:---:|:---:|:---:|:---:|
| Público (Portfólio) | 07/Dez/2025 | PTES · OSSTMM · RabbitSec | Comprometimento total (Root Shell) |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RESUMO ══════════════════════════ -->
<a id="resumo"></a>
## Resumo Executivo e Impacto

O sistema testado (**Meow** – IP `10.129.1.17`) apresentou uma falha crítica de configuração que permitiu a um atacante externo, sem credenciais iniciais, obter controle total do servidor (shell root) em poucos minutos após a enumeração de serviços.

A vulnerabilidade mais grave foi a **exposição direta do serviço Telnet (porta 23/tcp)**, configurado para permitir login direto como root (superusuário), sem exigir senha ou aceitando credenciais padrão. Esta falha de acesso direto ao privilégio máximo é uma das configurações de segurança mais negligentes e críticas.

A partir desse ponto de entrada inicial, foi possível:
- Obter uma sessão de terminal interativo com o usuário **root** (privilégios máximos)
- Acessar imediatamente arquivos sensíveis do sistema, incluindo a flag de comprometimento (`flag.txt`) em `/root`
- Demonstrar o comprometimento completo do servidor de forma instantânea

> **Risco:** Crítico (**CVSS 10.0/10**) — Comprometimento total do servidor

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ FALHAS ══════════════════════════ -->
<a id="falhas"></a>
## Falhas Críticas Encontradas (P0)

| ID | Título | Severidade | CVE / Referência | Ação no Ataque |
|----|--------|------------|------------------|----------------|
| **M-01** | Exposição do serviço Telnet permitindo login root direto | Crítica | Misconfiguration (OWASP A05:2021) | Acesso imediato como root (UID 0) |

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RELATÓRIO ══════════════════════════ -->
<a id="relatorio"></a>
## Relatório Completo

O relatório completo (metodologia, *timeline* visual e *proofs* detalhados) está disponível em:

<div align="center">

<a href="https://drive.google.com/file/d/1LAf9lfxStpVRk0boy80lkZZyj2mNtN4w/view?usp=sharing"><img src="https://img.shields.io/badge/📄_Ver_PDF_completo-1987F0?style=for-the-badge" alt="pdf"/></a>

</div>

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="../../README.md"><img src="https://img.shields.io/badge/◂_Voltar_ao_Portfólio-000000?style=for-the-badge&logo=github&logoColor=white" alt="portfolio"/></a>
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="perfil"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
</div>
