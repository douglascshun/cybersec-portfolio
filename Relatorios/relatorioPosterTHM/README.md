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

<h1 align="center">Relatório de Pentest — Máquina "Poster"</h1>
<p align="center"><em>TryHackMe · RabbitSec Red Team</em></p>

<div align="center">

<img src="https://img.shields.io/badge/Plataforma-TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=white" alt="thm"/>
<img src="https://img.shields.io/badge/Risco-CRÍTICO-d50000?style=for-the-badge" alt="risco"/>
<img src="https://img.shields.io/badge/CVE-2019--9193-d50000?style=for-the-badge" alt="cve"/>
<img src="https://img.shields.io/badge/Tempo_até_Root-<_2h-1987F0?style=for-the-badge" alt="tempo"/>

</div>

<!-- ══════════════════════════ NAVEGAÇÃO ══════════════════════════ -->
<div align="center">

<a href="#resumo"><img src="https://img.shields.io/badge/▸_RESUMO-1987F0?style=for-the-badge" alt="resumo"/></a>
<a href="#falhas"><img src="https://img.shields.io/badge/▸_FALHAS-000000?style=for-the-badge" alt="falhas"/></a>
<a href="#attack-path"><img src="https://img.shields.io/badge/▸_ATTACK_PATH-1987F0?style=for-the-badge" alt="attackpath"/></a>
<a href="#recomendacoes"><img src="https://img.shields.io/badge/▸_RECOMENDAÇÕES-000000?style=for-the-badge" alt="reco"/></a>
<a href="#relatorio"><img src="https://img.shields.io/badge/▸_PDF-1987F0?style=for-the-badge" alt="pdf"/></a>

</div>

<br/>

<div align="center">

| Classificação | Data do Teste | Metodologia |
|:---:|:---:|:---:|
| Público (Portfólio) | 22/Nov/2025 | OSSTMM · OWASP Testing Guide |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RESUMO ══════════════════════════ -->
<a id="resumo"></a>
## Resumo Executivo e Impacto

O objetivo foi comprometer o ativo **"Poster"** para avaliar a postura de segurança de um sistema de gerenciamento de banco de dados relacional (RDBMS) exposto.

O teste de invasão resultou em **comprometimento total do servidor (Root Shell)** em menos de 2 horas, devido a falhas críticas de configuração (P0) e credenciais padrão.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ FALHAS ══════════════════════════ -->
<a id="falhas"></a>
## Falhas Críticas Encontradas (P0)

| ID | Título | Severidade | Ação no Ataque |
|----|--------|------------|----------------|
| **P-01** | Exposição remota do PostgreSQL com credencial padrão | Crítica | Acesso inicial ao BD como `postgres` |
| **P-02** | RCE via PostgreSQL (`CVE-2019-9193`) | Crítica | Primeira shell como usuário `dark` |
| **P-05** | Privilégio sudo sem senha para o usuário `alison` | Crítica | Escalada de privilégios (Root) |

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ATTACK PATH ══════════════════════════ -->
<a id="attack-path"></a>
## Caminho Completo de Exploração (Attack Path)

Esta seção detalha os passos técnicos exatos para obter o controle total do sistema.

### Reconhecimento e Exploração Inicial (Initial Foothold)
1. **Varredura de Portas (Nmap):** identificação das portas TCP 22 (SSH), 80 (HTTP) e **5432 (PostgreSQL)** abertas.
2. **Enumerando PostgreSQL:** login bem-sucedido com a credencial padrão (`postgres:password`).
3. **Execução de Código Remoto (RCE):** acesso ao SO como `postgres` explorando a **`CVE-2019-9193`** (função `COPY FROM PROGRAM`).

### Movimentação Lateral e Credenciais
4. **Enumeração Local:** leitura de arquivos de configuração em busca de novas credenciais.
5. **Credenciais Hard-coded:** credenciais do usuário `dark` encontradas em arquivos de configuração da aplicação.
6. **Acesso SSH:** login via SSH com as credenciais de `dark`.

### Escalada de Privilégios (Privilege Escalation)
7. **Busca por Sudoers:** verificação dos comandos que `dark` pode executar como `sudo`.
8. **Movimentação para Alison:** descoberta de credenciais do usuário `alison`.
9. **Falha de Sudoers:** `alison` podia executar **TODOS** os comandos como `root` sem senha.
10. **Acesso a Root:** execução de `sudo su` / `sudo /bin/bash` para obter superusuário.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RECOMENDAÇÕES ══════════════════════════ -->
<a id="recomendacoes"></a>
## Recomendações Priorizadas

| Prioridade | Ação de Remediação | Prazo |
|------------|--------------------|-------|
| **P0 (Crítica)** | Bloquear a porta 5432 externamente (firewall) e alterar imediatamente a senha padrão do `postgres` | Imediato (máx. 24h) |
| **P1 (Alta)** | Remover o privilégio sudo sem senha (`ALL:ALL) ALL`) concedido ao usuário `alison` | 7 dias |
| **P1 (Alta)** | Remover credenciais *hard-coded* dos arquivos de configuração (ex: `config.php`) e migrar para um gerenciador de segredos / variáveis de ambiente | 7 dias |

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ RELATÓRIO ══════════════════════════ -->
<a id="relatorio"></a>
## Relatório Completo

O relatório completo (metodologia, *timeline* visual e *proofs* detalhados) está disponível em:

<div align="center">

<a href="https://drive.google.com/file/d/1w7nN38xmLuwFvaZ5JIydgQzCWH22YaVx/view?usp=sharing"><img src="https://img.shields.io/badge/📄_Ver_PDF_completo-1987F0?style=for-the-badge" alt="pdf"/></a>

</div>

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="../../README.md"><img src="https://img.shields.io/badge/◂_Voltar_ao_Portfólio-000000?style=for-the-badge&logo=github&logoColor=white" alt="portfolio"/></a>
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="perfil"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
</div>
