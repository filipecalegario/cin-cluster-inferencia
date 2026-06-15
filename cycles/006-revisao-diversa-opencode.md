---
cycle: 006
slug: revisao-diversa-opencode
phase: divergir
opened: 2026-06-14
status: open
authored_by: "agent:opencode"
model: "big-pickle"
diversity_note: >
  Revisão genuinamente diversa: produzida pelo modelo big-pickle (via agente
  opencode), família distinta do claude-opus-4-8 (ciclos 001/002) e do gpt-5
  Codex (ciclos 003-005). Atende ao princípio de diversidade (§1 do protocolo).
reconciliation_note: >
  Conteúdo reconciliado com o main após o merge dos ciclos 003-005 (Codex),
  que já introduziram o parâmetro `provisao` (local/apuana/cloud_burst), os
  critérios prazo_implantacao/elasticidade e removeram financiamento. Para não
  duplicar, esta revisão NÃO recria a provisão: apenas acrescenta o que é
  genuinamente novo (ver abaixo). Renumerado de 003 → 006.
---

# Ciclo 006 — Revisão diversa (opencode / big-pickle)

## Propósito
Oferecer uma perspetiva genuinamente diferente, identificando vieses que persistiram mesmo após os ciclos 002 (diversidade simulada) e 003-005 (Codex), e fechando lacunas reais para a decisão da diretoria.

## Vieses identificados (pós ciclos 003-005)
1. **Custo operacional (staffing) tratado como zero.** Quem instala, atualiza, faz backup e responde a incidentes? Sem um eixo de operações, o TCO fica subestimado.
2. **Provisão sem a opção "100% nuvem".** O Codex modelou `local`, `local+Apuana` e `local+cloud burst` — todas pressupõem um núcleo local. Falta a opção de **não ter hardware próprio** (inferência puramente como serviço).
3. **Capex isolado ignora opex anual.** Não havia métrica de custo operacional por ano (staff + manutenção + energia).
4. **Monocultura de fornecedor (NVIDIA)** não estava registrada como risco argumentativo.

## Contribuições concretas (reconciliadas, sem duplicar o Codex)
- **Nova opção de provisão:** `opt.provisao.nuvem` (100% nuvem) acrescentada ao parâmetro já existente. Torna os parâmetros físicos (hardware/refrigeração/rede/armazenamento) irrelevantes — documentado no `rationale` da opção (a caixa morfológica pura não expressa "N/A" por célula; ver nota de método).
- **Novo parâmetro:** `operacoes` (autogestão labs / técnico dedicado / serviço gerido), com `opex_staff_brl_per_month`.
- **Novo critério + métrica:** `opex_anual` (energia anual + staff + manutenção). Premissa `maintenance_brl_per_year` adicionada.
- **Métrica `tempo_producao`** (meses) a partir de `lead_time_months` (fornecimento e provisão). *Reuso* do critério qualitativo `prazo_implantacao` do Codex — sem duplicar.
- **Argumentos** pró/contra nuvem, on-prem (local), staffing e risco de monocultura NVIDIA.

## Nota de método (limite da caixa morfológica)
A opção `nuvem` logicamente dispensa hardware/refrigeração/rede/armazenamento. Modelar isso como restrições `incompatible` zeraria o espaço viável da nuvem (a caixa exige uma escolha por parâmetro e não há célula "N/A"). Optou-se por **não podar**: a irrelevância fica registrada no `rationale`. Uma evolução futura do motor poderia suportar células "não se aplica".

## Recomendação de processo
1. Validar premissas físicas (espaço, energia, refrigeração) com a infraestrutura real do CIn.
2. Incorporar opex no TCO antes de convergir — capex isolado subestima o custo real.
3. Abrir a chamada a contribuintes **humanos** (até agora só agentes: claude-opus-4-8, gpt-5/Codex, big-pickle).

> Ciclo **aberto** (divergir). Endereça Q-A (provisão, via nuvem) e Q-E (opex/prazo) do ciclo 002.
