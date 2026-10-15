# Scripting ofensivo em Python

> Nota de fundamentos · base para automatizar recon e brute force quando a ferramenta pronta não encaixa no alvo.

Python é a cola do trabalho ofensivo: quando o scanner genérico não serve, meia dúzia de linhas resolvem. As primitivas abaixo cobrem a maioria dos casos.

## Varredura de portas com sockets

```python
import socket

def porta_aberta(alvo, porta, timeout=1):
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        s.settimeout(timeout)
        return s.connect_ex((alvo, porta)) == 0
```

`connect_ex` devolve `0` em conexão bem-sucedida sem lançar exceção, o que deixa o laço limpo.

## Teste de autenticação web

```python
import requests

def tenta_login(url, usuario, senha):
    r = requests.post(url, data={"username": usuario, "password": senha}, timeout=3)
    return "Bem-vindo" in r.text   # ajustar ao marcador de sucesso do alvo
```

O sinal de sucesso muda por aplicação: às vezes é um texto, às vezes o status code, o header `Location` ou o tamanho da resposta. Identificar o marcador certo é metade do trabalho.

## Threading para acelerar

```python
from threading import Thread

for porta in (21, 22, 80, 443):
    Thread(target=varre, args=(alvo, porta)).start()
```

Para volume alto, trocar por `ThreadPoolExecutor` ou `asyncio` dá controle de concorrência sem estourar o alvo.

## Quebra de hash offline

```python
import hashlib

def quebra_md5(hash_alvo, wordlist):
    with open(wordlist) as f:
        for linha in f:
            palavra = linha.strip()
            if hashlib.md5(palavra.encode()).hexdigest() == hash_alvo:
                return palavra
    return None
```

MD5 sem salt cai rápido por dicionário. Em produção, isso é exatamente o antipadrão que a defesa precisa eliminar (ver nota de ICS e os relatórios de SUID/credenciais).

## Enquadramento de Red Team

- Script sob medida evita o ruído de ferramentas genéricas e reduz o que fica logado no alvo.
- Reutilização dessas primitivas vira tooling próprio: scanner de subdomínio, fuzzer de parâmetro, validador de credencial.
- Uso só em escopo autorizado. O mesmo código fora de um engajamento é crime.

[◂ Voltar aos Fundamentos](README.md)
