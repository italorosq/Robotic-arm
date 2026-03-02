# Projeto Braço Robótico

Repositório do desenvolvimento de um braço robótico com controle por visão computacional e comunicação entre ESPs usando ESP-NOW.

## Direção técnica

- Controle de motores distribuído em ESPs.
- Comunicação sem fio via ESP-NOW.
- Supervisão e tomada de decisão baseada em visão computacional.
- Estrutura enxuta para começar rápido e evoluir conforme o projeto avança.

## Estrutura de pastas

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

## Organização

- `hardware/eletronica`: esquemas, pinagem, ligações e lista de componentes.
- `hardware/redutor-planetario`: peças, e revisões do redutor planetário.
- `hardware/esqueleto`: estrutura mecânica principal do braço (bases, elos, suportes).
- `codigo/esp-firmware`: firmware dos ESPs (sem implementação neste momento).
- `codigo/visao-computacional`: scripts e experimentos de visão computacional (sem implementação neste momento).

## Próximos passos

1. Definir arquitetura de nós ESP (quem comanda cada motor).
2. Definir protocolo de mensagens ESP-NOW (IDs, comandos e telemetria).
3. Definir pipeline de visão computacional (entrada, detecção e saída de comando).

## Arquitetura 


1. Câmera e processamento de visão no computador identificam alvo/pose.
2. Computador gera comando de movimento (posição, velocidade ou ação).
3. ESP Mestre recebe/computa o comando final e distribui aos ESPs de atuadores via ESP-NOW.
4. ESPs de atuadores controlam motores locais e retornam telemetria.
5. ESP Mestre consolida estado e envia status para supervisão.

## Responsabilidades

- ESP Mestre (coordenação):
    - receber comando da camada de visão;
    - distribuir comandos para os nós de motor;
    - sincronizar ciclo de controle;
    - consolidar telemetria e estado do braço.

- ESP Atuador A (base/rotação):
    - controlar motor da junta da base;
    - reportar posição, velocidade e falhas.

- ESP Atuador B (ombro/cotovelo):
    - controlar motores dos elos principais;
    - reportar posição, velocidade e falhas.

- ESP Atuador C (punho/garra, opcional):
    - controlar extremidade (punho e efetuador final);
    - reportar posição, velocidade e falhas.

