# Cluster de inferência do CIn-UFPE — chamada aberta

Especificação **colaborativa** (humanos + agentes de IA) de uma infraestrutura de **inferência** para o Centro de Informática da UFPE. Este repositório é um **caso de uso** da plataforma [**idea-waddle**](https://github.com/filipecalegario/idea-waddle): as ideias vivem como uma **caixa morfológica** versionada em Git; um agente consolida as contribuições e um **site vivo** se atualiza a cada PR.

> Você dá *fork* aqui e manda *pull request* com ideias (opções, restrições, critérios). O motor que gera o site mora na plataforma idea-waddle — você não precisa mexer nele.

## O problema

O CIn já opera o **Apuana**, um cluster *batch* focado em **treinamento**. Esta chamada propõe projetar uma infraestrutura voltada a **inferência** — incluindo o experimento de prover um **LLM para a comunidade universitária**.

O objetivo é chegar a **caminhos de decisão** robustos e defensáveis — com estimativas de custo de capital, energia/mês e opções de aquisição de GPUs (mercado americano vs. chinês, fornecedores, parcerias) — para apresentar aos laboratórios e à diretoria do CIn.

## Estrutura

```
morphology/            ← a caixa morfológica viva
├── params/            ← um YAML por parâmetro (dimensão de decisão)
├── constraints.yaml   ← restrições de consistência (CCA) entre opções
├── criteria.yaml      ← critérios de avaliação (QOC)
└── assumptions.yaml   ← premissas das estimativas (tarifa, PUE, horas/mês)
cycles/                ← linha do tempo (NNN-slug.md por ciclo)
```

## Como contribuir

1. **Fork** deste repositório.
2. Edite/adicione um parâmetro, opção, restrição ou critério em `morphology/`, seguindo o **padrão de escrita** do [protocolo da idea-waddle](https://github.com/filipecalegario/idea-waddle/blob/main/AGENTS.md) (resumo em [`AGENTS.md`](AGENTS.md)).
3. Abra um **Pull Request**. A CI valida o padrão (lint) automaticamente; um humano responsável **ratifica** o merge. Nada é mesclado automaticamente.

Toda contribuição registra **proveniência** (quem / qual modelo). Diversidade — de visões humanas e de modelos — é princípio do projeto.

## Rodar localmente

O motor vem da plataforma idea-waddle. Clone-a ao lado e aponte para este caso:

```bash
git clone https://github.com/filipecalegario/idea-waddle ../idea-waddle
pip install pyyaml
IW_CASE="$PWD" IW_SITE="$PWD/site" python ../idea-waddle/engine/cca.py   # gera site/
IW_CASE="$PWD" python ../idea-waddle/engine/lint.py                       # valida o padrão
# abra site/cin-cluster-inferencia/index.html
```

Na nuvem, a CI ([`.github/workflows/build-site.yml`](.github/workflows/build-site.yml)) faz isso a cada PR e publica o site no GitHub Pages a cada push na `main`.
