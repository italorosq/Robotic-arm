# Código

![Domínio](https://img.shields.io/badge/dom%C3%ADnio-software-0a7ea4)
![Status](https://img.shields.io/badge/status-em%20planejamento-orange)

Nesta pasta, concentramos a parte de software do projeto: firmware embarcado, supervisão e integração com visão computacional.

## Escopo

- Desenvolvemos firmware dos nós ESP para controle distribuído de atuadores
- Implementamos pipeline de visão para detecção e geração de comandos
- Mantemos a interface de comunicação entre supervisor e rede ESP-NOW

## Estrutura

```text
codigo/
├── esp-firmware/
└── visao-computacional/
```

## Organização por módulo

- `esp-firmware`: desenvolvemos firmware do nó mestre e dos nós atuadores
- `visao-computacional`: desenvolvemos captura, processamento e emissão de comandos

## Marcos e prazos

| Etapa | Entrega | Status | Prazo alvo |
|---|---|---|---|
| C1 | Estrutura base dos módulos e convenções de código | Em andamento | 2026-03-15 |
| C2 | Definição e implementação inicial do protocolo de mensagens | Pendente | 2026-03-29 |
| C3 | Controle local de 1 atuador via firmware | Pendente | 2026-04-12 |
| C4 | Integração supervisor de visão + nó mestre | Pendente | 2026-04-26 |
| C5 | Validação de telemetria e fail-safe no fluxo completo | Pendente | 2026-05-10 |

## Critérios de aceite

### C1 - Estrutura base

- Definimos organização final de diretórios
- Documentamos convenções mínimas de versionamento e nomenclatura

### C2 - Protocolo

- Implementamos campos obrigatórios de comando, telemetria e heartbeat
- Verificamos compatibilidade de versão entre módulos

### C3 - Controle local

- Validamos resposta estável do atuador a setpoint
- Publicamos telemetria periódica sem falhas críticas

### C4 - Integração

- Validamos chegada de comando da visão ao nó atuador via nó mestre
- Registramos latência ponta a ponta em teste

### C5 - Validação

- Executamos fluxo completo com telemetria consolidada
- Validamos fail-safe em cenário de perda de comunicação
