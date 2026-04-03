# Visao Computacional

Subpasta para pipeline de visao que fecha a malha com o controle do braco.

## Escopo

- Captura de imagem da camera.
- Deteccao de alvo, pose ou ponto de interesse.
- Conversao de erro visual em comando para juntas.
- Envio de comando ao no mestre ESP32.

## Estrutura sugerida

```text
visao-computacional/
├── captura/
├── processamento/
├── controle/
├── integracao/
└── logs/
```

## Dependencias base

- Python 3.10+
- OpenCV
- Numpy
- Biblioteca de comunicacao com o no mestre

## Checklist de passos

- [ ] Definir camera e resolucao de trabalho.
- [ ] Implementar captura e calibracao basica.
- [ ] Implementar deteccao inicial do alvo.
- [ ] Calcular erro visual e mapear para setpoint de junta.
- [ ] Integrar envio de comando para o no mestre.
- [ ] Registrar latencia frame -> comando -> telemetria.
- [ ] Validar estabilidade da malha em teste controlado.
