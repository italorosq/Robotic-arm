# Projeto Braco Robotico em Malha Fechada

Projeto de um braco robotico controlado por multiplos ESP32 e supervisao por visao computacional.
O sistema usa malha fechada: a camera observa, o software calcula erro/acao e os ESP32 executam e retornam telemetria.

## Objetivos do projeto

- Controlar juntas do braco com resposta previsivel e repetivel.
- Implementar comunicacao entre nos ESP32 com baixa latencia.
- Fechar a malha com visao computacional para corrigir desvio de alvo/pose.
- Documentar hardware e software para facilitar evolucao do time.

## Arquitetura de alto nivel

1. Camera captura cena e envia frames para o modulo de visao.
2. Visao computacional detecta alvo/pose e calcula comando de movimento.
3. No mestre ESP32 recebe comando e distribui setpoints para nos atuadores.
4. Nos atuadores controlam motores e enviam telemetria de volta.
5. Supervisor consolida estado e ajusta comando no proximo ciclo.

## Estrutura do repositorio

```text
.
├── codigo/
│   ├── README.md
│   ├── esp-firmware/
│   │   └── README.md
│   └── visao-computacional/
│       └── README.md
├── hardware/
│   ├── README.md
│   ├── eletronica/
│   │   └── README.md
│   ├── esqueleto/
│   │   └── README.md
│   └── redutor-planetario/
│       └── README.md
└── README.md
```

## Lista BOM (resumo)

### BOM de hardware

- ESP32 DevKit (mestre + atuadores)
- Drivers de motor (ponte H ou driver de passo)
- Motores (DC com encoder ou stepper)
- Fonte de alimentacao separada para logica e potencia
- Conversores e protecoes (fusivel, TVS, capacitor de bulk)
- Camera (USB no host ou modulo dedicado)
- Estrutura mecanica, fixadores e redutor planetario

Detalhamento completo em hardware/eletronica/README.md.

### BOM de software

- Firmware ESP32 (Arduino ou ESP-IDF)
- Protocolo de comunicacao entre nos (ESP-NOW ou Wi-Fi local)
- OpenCV para visao computacional
- Python para supervisao e controle de alto nivel
- Serializacao de mensagens (JSON simples ou formato binario leve)

Detalhamento completo em codigo/README.md.

## Checklist de passos

- [ ] Definir topologia final de nos ESP32 (mestre e atuadores).
- [ ] Definir mapa de pinos e alimentacao por modulo.
- [ ] Montar prototipo eletrico minimo de 1 junta.
- [ ] Implementar protocolo de mensagens (comando, telemetria, heartbeat).
- [ ] Implementar controle local do atuador (posicao/velocidade).
- [ ] Implementar pipeline inicial de visao (detectar alvo e estimar erro).
- [ ] Integrar visao -> no mestre -> no atuador.
- [ ] Medir latencia fim a fim e estabilidade da malha.
- [ ] Validar fail-safe (perda de frame, perda de comunicacao, sobrecorrente).
- [ ] Documentar resultados de bancada e proxima iteracao.

## Como contribuir

1. Atualize a documentacao da pasta impactada.
2. Registre decisoes tecnicas e limites conhecidos.
3. Mantenha checklist e status sempre atualizados.

