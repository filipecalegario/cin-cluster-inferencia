---
cycle: 004
slug: modelo-energia
phase: divergir
opened: 2026-06-14
status: open
authored_by: "agent:codex"
model: "gpt-5 (Codex)"
---

# Ciclo 004 — Modelo de energia: teto térmico vs. operação típica

## Por que este ciclo existe
O caso já calcula capex e energia, mas o modelo anterior misturava duas coisas diferentes:

- **envelope térmico/elétrico** para infraestrutura;
- **consumo típico de operação** para pensar opex.

Usar `TDP × 24h × 30 dias` é defensável como **teto de dimensionamento**, mas é fraco como estimativa de conta de energia esperada de um serviço de inferência real. Em serving, utilização, batching, idle e perfil de carga importam.

## Contribuições incorporadas à caixa
- Em [`morphology/assumptions.yaml`](../morphology/assumptions.yaml), adicionei a premissa:
  - `load_factor_typical: 0.65`
- Em [`morphology/metrics.yaml`](../morphology/metrics.yaml), passei a distinguir:
  - `it_power_kw`
  - `power_kw` como potência total com PUE
  - `energy` como **teto térmico** mensal
  - `energy_typical` como estimativa mensal de **carga típica**
  - `energy_typical_year` como estimativa anual de energia

## Tese proposta para debate
O repositório deve parar de tratar um único número de energia como se ele servisse igualmente para:

1. dimensionar refrigeração e alimentação elétrica;
2. estimar opex recorrente;
3. comparar caminhos de aquisição.

Esses usos pedem números diferentes.

Minha proposta é simples e conservadora:

- manter o cálculo atual como **pior caso / teto térmico**;
- expor, ao lado dele, uma estimativa **típica** baseada em `load_factor_typical`;
- deixar explícito que esse fator ainda é premissa de planejamento, não medição do CIn.

## Limite importante desta proposta
`load_factor_typical: 0.65` **não é dado local medido**. É um placeholder deliberado para evitar que a conta mensal pareça mais precisa do que realmente é. O próximo salto de qualidade aqui não é discutir a segunda casa decimal: é incorporar um de dois artefatos reais:

- telemetria de um piloto de serving;
- fatura/contrato elétrico institucional aplicável ao ambiente onde o cluster ficará.

## Perguntas abertas para próximos ciclos
- O `load_factor_typical` deveria ser único para toda a caixa ou variar conforme perfil de acesso (`API`, `chat`, `ambos`)?
- Vale separar, em ciclo futuro, energia de **TI** e energia de **infraestrutura predial auxiliar** além do PUE simplificado?
- O caso deve introduzir um critério explícito de **opex anual** além dos cards quantitativos?
