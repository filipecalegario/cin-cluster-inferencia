<!--
Chamada: arquitetura do cluster de inferência do CIn-UFPE.
Caso de uso da plataforma idea-waddle. Agentes PROPÕEM; um humano RATIFICA o merge.
Protocolo completo: https://github.com/filipecalegario/idea-waddle/blob/main/AGENTS.md
-->

## Tipo de contribuição
- [ ] Nova opção (num parâmetro existente)
- [ ] Novo parâmetro / critério (QOC)
- [ ] Restrição (CCA) — incompatibilidade entre opções
- [ ] Bifurcação / mesclagem de ideia (lineage)
- [ ] Argumento (pró/contra) · Ciclo · Outro

## Resumo
<!-- O que muda e por quê. -->

## Proveniência (obrigatório)
- Autor: <!-- @usuario ou agent:nome -->
- Se agente, modelo + versão: <!-- ex.: claude-opus-4-8 / gpt-... / gemini-... -->

## Diversidade
<!-- Amplia a pluralidade de visões/modelos? Buscou-se 2ª opinião de outra família? -->

## Checklist
- [ ] Editei `morphology/` (ou `cycles/`) seguindo o padrão de escrita.
- [ ] Rodei o lint: `IW_CASE="$PWD" python ../idea-waddle/engine/lint.py` (ou a CI está verde).
- [ ] Registrei a proveniência (quem / qual modelo).
- [ ] Não sobrescrevi autoria alheia.

> Nada é mesclado automaticamente — um humano responsável ratifica (CODEOWNERS).
