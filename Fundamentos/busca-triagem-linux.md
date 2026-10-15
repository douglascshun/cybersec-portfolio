# Busca e triagem no Linux

> Nota de fundamentos · depois do foothold, caçar credenciais e vetores de escalada no sistema de arquivos.

Logo após o primeiro shell, o trabalho é triagem: achar segredos, configs e binários abusáveis no meio de milhares de arquivos. `grep`, `find` e `awk` são o tripé disso.

## Caçar padrões com `grep`

```bash
grep -ri "password" /var/www 2>/dev/null       # credenciais em código/config
grep -i "senha" /var/log/auth.log              # pistas em log de autenticação
```

`-r` recursivo, `-i` ignora caixa. Direcionar em `/var/www`, `/opt`, `/home` e `/etc` costuma render credenciais em texto claro (o pivô central do relatório da máquina Internal).

## Localizar arquivos com `find`

```bash
find / -name "*.conf" 2>/dev/null              # arquivos de configuração
find / -perm -4000 2>/dev/null                 # binários SUID (vetor de escalada)
find / -writable -type d 2>/dev/null           # diretórios graváveis
```

A busca por **SUID** (`-perm -4000`) é o primeiro reflexo na escalada de privilégio: um binário que roda como root e aceita abuso vira shell root (ver relatórios Mr Robot, Kenobi e Basic Pentesting).

## Fatiar texto com `awk`

```bash
awk -F: '{print $1}' /etc/passwd               # só os nomes de usuário
awk -F: '$3 >= 1000 {print $1}' /etc/passwd    # contas de usuário humano
```

`awk` transforma saída crua em lista limpa para o próximo passo, melhor que recortar na mão.

## Enquadramento de Red Team

- Essas três ferramentas são nativas: não exigem upload, deixam pouco rastro e não disparam alerta de binário estranho.
- A ordem prática pós-foothold: ler configs e logs (`grep`), inventariar SUID e permissões (`find`), normalizar o resultado (`awk`).
- Do lado defensivo, é o mesmo arsenal para auditoria: inventariar SUID, caçar segredo hardcoded e revisar permissão de diretório antes que o atacante faça.

[◂ Voltar aos Fundamentos](README.md)
