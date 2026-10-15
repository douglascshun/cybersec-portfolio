# Segurança de ICS/SCADA

> Nota de fundamentos · onde o ataque deixa de ser dado e vira impacto físico.

Sistemas de controle industrial (ICS) e supervisão (SCADA) operam usinas, fábricas e utilities. A diferença para TI corporativa é o impacto: aqui um comando errado move um atuador no mundo real. Muitos protocolos de OT nasceram sem autenticação, o que torna a enumeração perigosamente barata para o atacante.

## Arquitetura típica (e sua fragilidade)

```
PLC  <->  HMI  <->  Rede corporativa  <->  Internet
```

O elo fraco costuma ser a ponte entre a rede corporativa e a de OT: quando não há segmentação, um foothold em TI alcança o PLC.

## Enumeração de dispositivos

```bash
nmap -sU -p 161,102 <faixa>/24     # SNMP (161) e IEC 61850 (102)
```

- `161/udp` · SNMP, frequentemente com community string padrão (`public`).
- `102/tcp` · IEC 61850 / S7, protocolo de automação.
- `502/tcp` · Modbus, o clássico sem autenticação.

## Protocolos industriais

```bash
# Leitura de registros Modbus
modbus read <ip_plc> 1 0 10

# Detecção via Metasploit
use auxiliary/scanner/scada/modbusdetect
set RHOSTS <ip_plc>
run
```

Modbus e DNP3, por padrão, não autenticam nem cifram: quem alcança a rede lê e, muitas vezes, escreve registros.

## Casos reais

- **Stuxnet (2010):** sabotou centrífugas nucleares manipulando PLCs Siemens.
- **Triton (2017):** atacou o sistema instrumentado de segurança (SIS) de uma planta química, mirando o mecanismo que deveria evitar acidente.

Ambos mostram o ponto: o alvo final não é o dado, é o processo físico.

## Defesa

```bash
# Segmentar: bloquear protocolo industrial saindo para a rede corporativa
iptables -A FORWARD -p tcp --dport 102 -j DROP

# Permitir Modbus apenas a partir da HMI autorizada
iptables -A INPUT -s <ip_hmi> -p tcp --dport 502 -j ACCEPT
```

- Segmentação de rede (IT/OT) é a primeira e mais efetiva barreira.
- Monitoramento especializado (ex.: Nozomi, Siemens SINEC IDS) entende protocolo de OT, que IDS corporativo ignora.
- TI industrial não é TI corporativa: patch quebra linha de produção, então a defesa se apoia em isolamento e visibilidade, não só em atualização.

[◂ Voltar aos Fundamentos](README.md)
