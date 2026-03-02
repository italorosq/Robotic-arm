# Projeto Braço Robótico

![Fase](https://img.shields.io/badge/fase-estrutura%C3%A7%C3%A3o-blue)
![Status](https://img.shields.io/badge/status-em%20desenvolvimento-orange)
![Licença](https://img.shields.io/badge/licen%C3%A7a-pendente-lightgrey)

Neste repositório, construímos um braço robótico com controle distribuído em ESPs, comunicação via ESP-NOW e integração com visão computacional.

## Escopo técnico

- Controlamos as juntas com nós embarcados independentes
- Trocamos comandos e telemetria entre nós via ESP-NOW
- Integramos visão computacional para gerar comandos de movimento
- Registramos telemetria para monitoramento e diagnóstico

## Estrutura do repositório

```text
.
├── codigo/
│   ├── esp-firmware/
│   └── visao-computacional/
└── hardware/
    ├── eletronica/
    ├── esqueleto/
    └── redutor-planetario/
```

## Organização por domínio

- `codigo/esp-firmware`: mantemos o firmware dos nós embarcados
- `codigo/visao-computacional`: mantemos captura, processamento e emissão de comandos
- `hardware/eletronica`: mantemos esquemas elétricos, pinagem e BOM
- `hardware/esqueleto`: mantemos estrutura mecânica, suportes e interfaces
- `hardware/redutor-planetario`: mantemos documentação e arquivos do redutor

## Arquitetura operacional

1. Capturamos a cena e estimamos alvo/pose no módulo de visão.
2. Convertemos a saída da visão em comandos de movimento.
3. Distribuímos comandos do nó mestre para os nós atuadores via ESP-NOW.
4. Executamos controle local das juntas nos nós atuadores.
5. Consolidamos telemetria no nó mestre para supervisão.

## Topologia de nós

- `ESP Mestre`: coordenamos o ciclo de controle, roteamos comandos e agregamos telemetria
- `ESP Atuador A`: controlamos a junta da base
- `ESP Atuador B`: controlamos as juntas de ombro e cotovelo
- `ESP Atuador C` (opcional): controlamos punho e garra

## Contrato mínimo de mensagens

- `Comando`: id do nó, tipo de ação, setpoint, limite de velocidade, timestamp
- `Telemetria`: id do nó, posição atual, velocidade atual, erro/corrente, timestamp
- `Heartbeat`: presença do nó e estado da comunicação

## Requisitos de engenharia

- Garantimos falha segura em caso de perda de comunicação
- Mantemos payload compatível com os limites do ESP-NOW
- Trabalhamos com frequência de atualização determinística no ciclo de controle
- Versionamos o protocolo para manter compatibilidade entre nós

## Marcos e prazos

| Etapa | Entrega | Status | Prazo alvo |
|---|---|---|---|
| M1 | Mapa de atuadores e topologia final de nós | Em andamento | 2026-03-15 |
| M2 | Protocolo ESP-NOW versionado (comando, telemetria, heartbeat) | Pendente | 2026-03-29 |
| M3 | Controle local estável em bancada (1 junta) | Pendente | 2026-04-12 |
| M4 | Integração visão computacional + ESP mestre | Pendente | 2026-04-26 |
| M5 | Validação fim a fim com fail-safe e telemetria | Pendente | 2026-05-10 |

## Critérios de aceite por etapa

### M1 - Arquitetura de nós

- Documentamos a topologia de nós no repositório
- Definimos a junta atendida por cada nó
- Definimos a interface entre supervisor e nó mestre

### M2 - Protocolo de mensagens

- Documentamos os pacotes com campos e tipos
- Declaramos e validamos a versão do protocolo
- Executamos teste de envio e recebimento entre pelo menos 2 nós

### M3 - Controle local

- Validamos resposta da junta de teste a setpoint de posição e velocidade
- Entregamos telemetria periódica sem perda crítica
- Validamos fail-safe em perda de comunicação

### M4 - Integração com visão

- Garantimos que o pipeline de visão gere comando compatível com o protocolo
- Validamos recepção e distribuição de comandos pelo nó mestre
- Registramos latência ponta a ponta

### M5 - Validação fim a fim

- Executamos ciclo completo com pelo menos 2 juntas
- Consolidamos telemetria no nó mestre sem inconsistências
- Aprovamos procedimentos de falha segura em teste funcional

## Licença

Ainda não definimos a licença.

