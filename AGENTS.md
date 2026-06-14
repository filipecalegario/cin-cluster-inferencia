# AGENTS.md — caso: cluster de inferência do CIn-UFPE

> Este é um **caso de uso** da plataforma [idea-waddle](https://github.com/filipecalegario/idea-waddle).
> O **protocolo de colaboração canônico** (tipos de contribuição, padrão de escrita, como agentes processam o conteúdo) está em
> **[idea-waddle/AGENTS.md](https://github.com/filipecalegario/idea-waddle/blob/main/AGENTS.md)** — leia-o antes de contribuir. Abaixo, só o essencial e o contexto do caso.

## Contexto do problema
Projetar, de forma colaborativa (humanos + agentes), uma infraestrutura de **inferência** para o CIn-UFPE (complementando o cluster *batch* "Apuana"), incluindo prover um **LLM para a comunidade**. Entregável: **caminhos de decisão** com estimativas de custo/energia e opções de aquisição de GPUs, para a diretoria do CIn. Histórico e decisões: `cycles/`.

## Princípios (não negociáveis)
1. **Diversidade** de visões humanas e de modelos; nenhum modelo único deve dominar.
2. **Rastreabilidade**: toda opção/restrição/critério registra `proposed_by`/`by`; se for agente (`agent:nome`), declarar `model`.
3. **Human-in-the-loop**: agentes propõem via PR; um humano ratifica o merge. Nada é auto-mesclado.

## O que você edita (em `morphology/`)
- `params/NN-*.yaml` — parâmetros e suas opções.
- `constraints.yaml` — incompatibilidades (CCA) entre opções de parâmetros **diferentes**.
- `criteria.yaml` — critérios de avaliação (QOC); `assumptions.yaml` — premissas das estimativas.
- `cycles/NNN-slug.md` — registro de ciclo (front-matter YAML obrigatório).

## Exemplo mínimo de opção
```yaml
- id: opt.<param>.<slug>
  label: "Rótulo curto"
  proposed_by: "@usuario"        # ou agent:nome
  model: "claude-opus-4-8"       # obrigatório se agente
  status: proposed               # proposed | accepted | superseded | rejected
  rationale: "Por que esta opção."
  scores: { sustentabilidade: 4 }   # 1-5, opcional
```

## Antes de abrir o PR
Rode o validador (mesmo da CI):
```bash
IW_CASE="$PWD" python ../idea-waddle/engine/lint.py
```
Erros (✗) bloqueiam o merge; avisos (⚠) não. Detalhes do padrão: protocolo da idea-waddle (link acima).
