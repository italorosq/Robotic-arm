# Hardware

Camada fisica do projeto: eletronica de controle/potencia, estrutura mecanica e transmissao com redutor planetario.

## Estrutura

```text
hardware/
├── eletronica/
├── esqueleto/
└── redutor-planetario/
```

## Objetivo da pasta

- Garantir alimentacao e acionamento seguro dos atuadores.
- Garantir estrutura mecanica rigida e alinhada.
- Integrar redutor para aumento de torque e resolucao.

## Lista BOM de hardware (macro)

- 2 a 4 placas ESP32 DevKit
- Drivers de motor conforme tipo de atuador
- Fonte de potencia para motores
- Fonte regulada para logica 5V/3.3V
- Encoder ou sensor de realimentacao de junta
- Cabos, conectores, borne e protecoes
- Pecas impressas 3D do esqueleto e acoplamentos
- Conjunto de redutor planetario e fixadores

Detalhamento por item em hardware/eletronica/README.md e hardware/esqueleto/README.md.

## Checklist de implementacao (hardware)

- [ ] Definir corrente maxima por atuador e dimensionar drivers.
- [ ] Definir arquitetura de alimentacao (logica isolada de potencia).
- [ ] Definir pinagem completa dos ESP32 por junta.
- [ ] Montar bancada eletrica minima com 1 atuador.
- [ ] Verificar ruido, queda de tensao e aquecimento.
- [ ] Montar estrutura mecanica base e validar alinhamento.
- [ ] Integrar redutor planetario na junta alvo.
- [ ] Validar backlash e repetibilidade mecanica.
- [ ] Registrar revisao da montagem e pendencias.
