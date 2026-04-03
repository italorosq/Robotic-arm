# Codigo

Camada de software do projeto: firmware dos ESP32, visao computacional e logica de supervisao em malha fechada.

## Estrutura

```text
codigo/
├── esp-firmware/
└── visao-computacional/
```

## Responsabilidades por modulo

- esp-firmware: controle local das juntas, comunicacao entre nos e telemetria.
- visao-computacional: captura de imagem, deteccao de alvo/pose e geracao de comando.

## Lista BOM de software

### Firmware (ESP32)

- Framework: Arduino Core para ESP32 ou ESP-IDF
- Comunicacao: ESP-NOW (ou Wi-Fi local como alternativa)
- Bibliotecas de controle: PID, filtro e encoder conforme atuador

### Visao e supervisao

- Python 3.10+
- OpenCV
- Numpy
- Biblioteca de comunicacao com no mestre (serial, UDP ou MQTT local)
- Ferramenta de log e plot (csv + script, ou dashboard simples)

## Interface minima entre visao e firmware

- Comando: id_junta, setpoint, modo_controle, timestamp.
- Telemetria: posicao, velocidade, corrente estimada, status_falha, timestamp.
- Heartbeat: versao_protocolo, uptime, estado do no.

## Checklist de implementacao (software)

- [ ] Definir formato de mensagem e versao do protocolo.
- [ ] Criar firmware base do no mestre com roteamento de comandos.
- [ ] Criar firmware base de 1 no atuador com telemetria.
- [ ] Implementar watchdog e fail-safe nos nos.
- [ ] Implementar pipeline de visao com deteccao inicial.
- [ ] Converter erro de visao em comando de junta.
- [ ] Integrar fluxo completo com log de latencia.
- [ ] Criar testes de regressao para protocolo e parse de mensagens.

## Entrega minima valida

1. Um alvo detectado em video gera setpoint de movimento.
2. No mestre encaminha comando para 1 atuador.
3. Atuador executa e retorna telemetria estavel por pelo menos 5 minutos.
