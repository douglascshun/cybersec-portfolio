# 🛡️ Relatório de Teste de Invasão:   Máquina "Poster" (TryHackMe)

**Classificação:** Público (Portfólio)  
**Data do Teste:** 22 de Novembro de 2025  
**Metodologia:** OSSTMM e OWASP Testing Guide

## 2. Resumo Executivo e Impacto

O objetivo foi comprometer o ativo "Poster" para avaliar a postura de segurança de um sistema de gerenciamento de banco de dados relacional (RDBSM) exposto.

O teste de invasão resultou em **comprometimento total do servidor (Root Shell)** em menos de 2 horas devido a falhas críticas de configuração (P0) e credenciais padrão.

### Falhas Críticas Encontradas (P0)

| ID | Título | Severidade | Ação no Ataque |
| :--- | :--- | :--- | :--- |
| **P-01** | Exposição remota do PostgreSQL com credencial padrão | Crítica | Acesso inicial ao BD como `postgres`. |
| **P-02** | RCE via PostgreSQL (CVE-2019-9193) | Crítica | Usado para obter a primeira shell como usuário `dark`. |
| **P-05** | Privilégio sudo sem senha para usuário `alison` | Crítica | Usado para Escalada de Privilégios (Root). |

---

## 6. Caminho Completo de Exploração (Attack Path)

Esta seção detalha os passos técnicos exatos para obter o controle total do sistema.

### 6.1. Reconhecimento e Exploração Inicial (Initial Foothold)

1.  **Varredura de Portas (Nmap):** Identificação das portas TCP 22 (SSH), 80 (HTTP) e **5432 (PostgreSQL)** abertas.
2.  **Enumerando PostgreSQL:** Tentativa bem-sucedida de login no PostgreSQL com a credencial padrão (`postgres:password`).
3.  **Execução de Código Remoto (RCE):** Acesso ao sistema operacional como usuário `postgres` explorando a vulnerabilidade **CVE-2019-9193** (função `COPY FROM PROGRAM`).

### 6.2. Movimentação Lateral e Credenciais

4.  **Enumeração Local:** Leitura de arquivos de configuração para encontrar novas credenciais.
5.  **Credenciais Hard-coded:** Credenciais de usuário (`dark`) encontradas em arquivos de configuração da aplicação.
6.  **Acesso SSH:** Login via SSH usando as credenciais do usuário `dark`.

### 6.3. Escalada de Privilégios (Privilege Escalation)

7.  **Busca por Sudoers:** Verificação de comandos que o usuário `dark` pode executar como `sudo`.
8.  **Movimentação para Alison:** Descoberta de credenciais para o usuário `alison`.
9.  **Falha de Sudoers:** O usuário `alison` estava configurado para executar **TODOS** os comandos como `root` sem a necessidade de senha.
10. **Acesso a Root:** Execução de `sudo su` ou `sudo /bin/bash` para obter acesso de superusuário.

---

## 8. Recomendações Priorizadas

| Prioridade | Ação de Remediação | Prazo |
| :--- | :--- | :--- |
| **P0 (Crítica)** | Bloquear a porta 5432 externamente (firewall) e alterar imediatamente a senha padrão do `postgres`. | Imediato (Máx. 24h) |
| **P1 (Alta)** | Remover o privilégio sudo sem senha (`ALL:ALL) ALL`) concedido ao usuário `alison`. | 7 dias |
| **P1 (Alta)** | Remover credenciais *hard-coded* de todos os arquivos de configuração (ex: `config.php`) e migrar para um gerenciador de segredos ou variáveis de ambiente. | 7 dias |

## 🔗 Referência

O relatório completo (incluindo metodologia, *timeline* visual e *proofs* detalhados) está disponível no arquivo:
[relatorioPosterRabbitSec.pdf](https://drive.google.com/file/d/1w7nN38xmLuwFvaZ5JIydgQzCWH22YaVx/view?usp=sharing)
