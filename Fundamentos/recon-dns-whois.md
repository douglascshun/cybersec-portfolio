# Reconhecimento com DNS e WHOIS

> Nota de fundamentos · mapear infraestrutura e superfície de ataque antes de tocar no alvo.

Antes de qualquer exploração vem o mapa. DNS e WHOIS entregam infraestrutura, e-mail, subdomínios e dados de registro sem mandar um pacote sequer para o alvo final (recon passivo).

## Registros DNS com `dig`

```bash
dig alvo.com ANY +noall +answer      # visão ampla (A, MX, TXT...)
dig alvo.com MX +short               # servidores de e-mail
dig alvo.com TXT +short              # SPF/DKIM, verificações de serviço
```

`MX` revela o provedor de e-mail (vetor de phishing). `TXT` costuma vazar quais serviços SaaS a empresa usa.

## Dados de registro com `whois`

```bash
whois alvo.com
# Registrant, Registrar, Creation Date, nameservers
```

Expõe dono, data de criação e, quando não há proteção de privacidade, nome e contato. Útil para engenharia social e para datar a infraestrutura.

## DNS reverso com `host`

```bash
host 203.0.113.10
# 10.113.0.203.in-addr.arpa domain name pointer alvo.com
```

Reverso ajuda a confirmar faixas de IP e a amarrar hosts a uma organização.

## Enquadramento de Red Team

- Tudo aqui é passivo ou quase: baixo risco de detecção, feito antes de escanear portas.
- DNS revela o que não está no site: subdomínios de homologação, VPN, correio, painéis.
- Do lado defensivo: minimizar o que o DNS/WHOIS publicam, usar privacy no registro e vigiar enumeração de subdomínio é reduzir superfície antes do atacante olhar.

[◂ Voltar aos Fundamentos](README.md)
