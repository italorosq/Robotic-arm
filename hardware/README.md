# Hardware

![Domínio](https://img.shields.io/badge/dom%C3%ADnio-hardware-5b8c00)
![Status](https://img.shields.io/badge/status-em%20organiza%C3%A7%C3%A3o-orange)

Nesta pasta, organizamos a parte de hardware: eletrônica, estrutura mecânica e transmissão com redutor planetário.

## Escopo

- Definimos e documentamos arquitetura elétrica
- Desenvolvemos a estrutura mecânica do braço e os pontos de montagem
- Integramos o conjunto de transmissão e redução nas juntas

## Estrutura

```text
hardware/
├── eletronica/
├── esqueleto/
└── redutor-planetario/
```

## Organização por módulo

- `eletronica`: mantemos esquemas, pinagem, ligações e BOM
- `esqueleto`: mantemos peças estruturais, suportes e interfaces mecânicas
- `redutor-planetario`: mantemos arquivos de referência, documentação e créditos de origem

## Marcos e prazos

| Etapa | Entrega | Status | Prazo alvo |
|---|---|---|---|
| H1 | Estrutura de pastas e baseline de documentação | Em andamento | 2026-03-15 |
| H2 | Definição de arquitetura elétrica e mapeamento de I/O | Pendente | 2026-03-29 |
| H3 | Conjunto mecânico base validado em montagem | Pendente | 2026-04-12 |
| H4 | Integração mecânica do redutor nas juntas principais | Pendente | 2026-04-26 |
| H5 | Validação de operação mecânica com carga de teste | Pendente | 2026-05-10 |

## Critérios de aceite

### H1 - Baseline

- Finalizamos a estrutura de domínios
- Criamos documentação mínima por submódulo

### H2 - Eletrônica

- Revisamos esquema elétrico e pinagem
- Consolidamos lista de materiais inicial

### H3 - Esqueleto

- Montamos peças principais sem interferência mecânica crítica
- Validamos fixação e alinhamento dos componentes

### H4 - Redutor

- Concluímos acoplamento do redutor nas juntas críticas
- Avaliamos folga e transmissão em teste funcional

### H5 - Validação

- Executamos teste de bancada contínuo sem falha mecânica crítica
- Documentamos ajustes mecânicos e lições aprendidas
