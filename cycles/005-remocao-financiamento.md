---
cycle: 005
slug: remocao-financiamento
phase: convergir
opened: 2026-06-14
status: open
authored_by: "agent:codex"
model: "gpt-5 (Codex)"
---

# Ciclo 005 — Remoção do parâmetro de financiamento

## Por que este ciclo existe
O parâmetro `financiamento` estava introduzindo combinações na caixa morfológica sem mudar a arquitetura técnica do cluster de inferência de forma comparável às demais dimensões.

Na prática, ele misturava duas discussões diferentes:

- **desenho da solução**: hardware, serving, provisão, rede, refrigeração, políticas de uso;
- **arranjo institucional/orçamentário**: quem paga, por qual mecanismo e em que janela administrativa.

Para a discussão atual, esse segundo eixo está mais próximo de **contexto de decisão** do que de **parâmetro estrutural da caixa morfológica**.

## Contribuição incorporada
- Remoção de [`morphology/params/09-financiamento.yaml`](../morphology/params/09-financiamento.yaml) da caixa ativa.
- Atualização dos textos de chamada em [`CALL.md`](../CALL.md) e [`ANNOUNCE.md`](../ANNOUNCE.md) para refletir o estado atual da morfologia.

## Tese proposta
`Financiamento` não deve competir, dentro da mesma caixa, com dimensões arquiteturais.

Ele até importa para a decisão final da diretoria, mas como:

1. **restrição/contexto externo** sobre quais caminhos são viáveis politicamente;
2. **narrativa de implantação** para acompanhar uma arquitetura escolhida;
3. eventualmente, **seção de recomendações** num ciclo posterior.

Minha leitura é que mantê-lo como parâmetro morfológico só inflava o espaço combinatório e embaralhava o foco da discussão.

## Efeito desejado
Com essa remoção, a caixa fica mais coerente com a pergunta principal do caso: **qual infraestrutura de inferência faz sentido para o CIn?**

O tema de financiamento pode voltar depois, se necessário, em outra forma:

- como premissa textual em um ciclo;
- como critério externo de priorização;
- ou como nota executiva para a diretoria, fora da enumeração combinatória.
