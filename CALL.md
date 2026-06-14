# Chamada aberta — arquitetura do cluster de inferência do CIn-UFPE

**Convite a humanos e agentes** para co-projetar a infraestrutura de inferência do Centro de Informática da UFPE. As ideias são consolidadas numa **caixa morfológica viva** (opções × restrições) e apresentadas como **caminhos de decisão** aos laboratórios e à diretoria do CIn.

## Por que participar
- O CIn vai decidir sobre um investimento real (GPUs, energia, operação). Quanto mais perspectivas — técnicas, econômicas, de sustentabilidade, de soberania — melhor a decisão.
- Tudo é **rastreável**: sua contribuição fica registrada com autoria no histórico do Git.
- **Diversidade é o ponto**: queremos visões humanas variadas e modelos de IA diferentes, sem que uma só voz domine.

## O que estamos decidindo
Parâmetros já em aberto (veja a caixa viva): hardware de aceleração, origem de fornecimento, software de serving, escala, rede, modelo de acesso, refrigeração/energia, armazenamento, financiamento, modelos de LLM a servir, políticas de uso. Faltam, entre outros: critérios de opex e prazo, pegada de carbono, federação com o Apuana, provisão on-prem × nuvem.

## Como contribuir (resumo)
1. Dê **fork** e edite `morphology/` (uma opção, uma restrição, um critério) ou abra um ciclo em `cycles/`.
2. Siga o **padrão de escrita** (ver [`AGENTS.md`](AGENTS.md)) e registre sua **proveniência**.
3. Abra um **Pull Request**. A CI valida; um humano ratifica. O site vivo atualiza no merge.

## Formas de contribuir
- **Nova opção** num parâmetro · **novo parâmetro** · **restrição** (incompatibilidade) · **critério/estimativa** · **argumento** pró/contra · **segunda opinião** de outra família de modelos.

## Linha do tempo
Cada ciclo é um arquivo `cycles/NNN-slug.md`. Estamos em fase de **divergência** (abrir possibilidades) antes de convergir para os caminhos de decisão.

> Dúvidas ou para coordenar uma rodada de revisão por uma família de modelo diferente: abra uma *issue*.
