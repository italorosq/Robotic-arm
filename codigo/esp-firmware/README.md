# ESP Firmware

Subpasta para firmware dos nos ESP32 do braco robotico.

## Escopo

- No mestre: recebe comandos da supervisao e distribui para atuadores.
- Nos atuadores: executam controle local de cada junta.
- Telemetria: reporta estado, falhas e heartbeat.

## Estrutura sugerida

```text
esp-firmware/
├── mestre/
├── atuador-base/
├── atuador-braco/
├── common/
└── docs/
```

## Requisitos minimos de firmware

- Laço de controle local por junta.
- Timeout de comando para fail-safe.
- Heartbeat periodico para no mestre.
- Mensagens com timestamp e versao de protocolo.

## Checklist de passos

- [ ] Definir modo de controle por junta (posicao/velocidade).
- [ ] Definir pacote de comando e pacote de telemetria.
- [ ] Implementar firmware base do no mestre.
- [ ] Implementar firmware base de 1 no atuador.
- [ ] Validar comunicacao em bancada por 10 minutos sem perda critica.
- [ ] Implementar watchdog e estado seguro de parada.
- [ ] Escalar para multiplos atuadores.
