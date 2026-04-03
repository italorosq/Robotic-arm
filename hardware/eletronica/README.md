# Eletronica

Subpasta para esquemas, pinagem, alimentacao e protecao eletrica do sistema.

## Lista BOM (detalhada)

| Item | Quantidade inicial | Observacao |
|---|---:|---|
| ESP32 DevKit | 2 a 4 | 1 mestre + 1 por grupo de juntas |
| Driver de motor | 1 por atuador | Escolher conforme tipo de motor |
| Fonte de potencia | 1 | Dimensionar pela corrente total dos motores |
| Regulador 5V/3.3V | 1 por dominio | Separar logica e potencia quando possivel |
| Encoder/Sensor de posicao | 1 por junta critica | Realimentacao para controle local |
| Fusivel e protecao TVS | Conforme projeto | Protecao contra surto e curto |
| Capacitor de bulk | Conforme corrente | Reduzir afundamento de tensao |
| Bornes e conectores | Conforme montagem | Facilitar manutencao |
| Cabos e malha de aterramento | Conforme montagem | Reduzir ruido e interferencia |

## Pinagem minima para iniciar

- UART/Serial de debug no no mestre.
- GPIOs de PWM/direcao para driver de motor.
- Entradas de encoder ou sensor de posicao.
- Linha de enable para estado seguro.

## Checklist de passos

- [ ] Fechar diagrama eletrico inicial do no mestre.
- [ ] Fechar diagrama eletrico inicial de 1 no atuador.
- [ ] Revisar correntes de pico e dissipacao termica.
- [ ] Montar bancada com alimentacao separada de logica e potencia.
- [ ] Testar protecao (fusivel, inversao e ruido).
- [ ] Publicar revisao da BOM com codigos de compra.
