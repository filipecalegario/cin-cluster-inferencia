# Material de divulgação — chamada aberta

Textos prontos para compartilhar. Ajuste tom/extensão conforme o canal. Links:
- **Caixa morfológica viva:** https://filipecalegario.github.io/cin-cluster-inferencia/
- **Repositório (forke e contribua):** https://github.com/filipecalegario/cin-cluster-inferencia
- **Plataforma (motor + protocolo):** https://github.com/filipecalegario/idea-waddle

---

## Versão curta (redes sociais)
🧩 Chamada aberta: ajude a projetar o **cluster de inferência do CIn-UFPE**.
Humanos **e** agentes de IA propõem ideias via Git; uma **caixa morfológica viva** consolida opções, restrições e estimativas de custo/energia — tudo rastreável.
Explore e contribua 👉 https://filipecalegario.github.io/cin-cluster-inferencia/

## Versão média (LinkedIn / lista)
O Centro de Informática da UFPE quer especificar, de forma **aberta e colaborativa**, uma infraestrutura de **inferência** (complementar ao cluster Apuana, de treinamento) — incluindo prover um LLM para a comunidade.

A novidade é o **como**: usamos o Git como espinha dorsal de uma colaboração entre **humanos e agentes de IA**. As contribuições viram uma **caixa morfológica** (método de análise morfológica de Zwicky) com restrições de consistência e estimativas de custo de capital, energia/mês e opções de aquisição de GPUs. Um **site vivo** se atualiza a cada contribuição, e tudo é rastreável (quem — e qual modelo — propôs o quê). Princípio central: **diversidade** de visões e de modelos, sem que uma só voz domine.

Explore a caixa viva e mande seu *pull request*:
- Site: https://filipecalegario.github.io/cin-cluster-inferencia/
- Repo: https://github.com/filipecalegario/cin-cluster-inferencia

## Versão e-mail (laboratórios / diretoria do CIn)
Assunto: Chamada aberta — arquitetura do cluster de inferência do CIn

Prezados,

Estamos abrindo uma chamada colaborativa para especificar o cluster de **inferência** do CIn (complementar ao Apuana). A proposta reúne contribuições de pesquisadores e de agentes de IA num repositório Git, consolidadas numa **caixa morfológica viva** que mostra as opções (hardware, fornecimento, rede, refrigeração, financiamento, modelos a servir, políticas de uso…), suas incompatibilidades e estimativas de custo/energia. O objetivo é chegar a **caminhos de decisão** defensáveis para apresentação à diretoria.

Como participar (5 min): explore o site vivo e abra uma issue/PR.
- Site: https://filipecalegario.github.io/cin-cluster-inferencia/
- Repositório e como contribuir: https://github.com/filipecalegario/cin-cluster-inferencia

Quanto mais diversa a participação, melhor a decisão. Contamos com vocês.

## Primeiras contribuições sugeridas (good first issues)
- Critérios ausentes: **opex/ano**, **prazo até produção**, **pegada de carbono**.
- Parâmetro **provisão**: on-prem × nuvem (cloud burst) × híbrido.
- **Federação com o Apuana** (usar janelas ociosas).
- Refinar **premissas** das estimativas (tarifa de energia real de PE, preços de GPU, PUE).
- Contestar restrições (ex.: InfiniBand × Ascend é mesmo *hard*?) — abrir argumento.
- **Segunda opinião** por uma família de modelo diferente (ver `cycles/002`).
