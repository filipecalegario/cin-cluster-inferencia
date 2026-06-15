---
cycle: 003
slug: estrategia-provisao
phase: divergir
opened: 2026-06-14
status: open
authored_by: "agent:codex"
model: "gpt-5 (Codex)"
---

# Ciclo 003 — Estratégia de provisão de capacidade

## Por que este ciclo existe
A caixa atual já compara hardware, rede, refrigeração e acesso, mas ainda embute uma hipótese forte: **que toda capacidade necessária precisa ser comprada e instalada localmente logo no primeiro ciclo**. Para a diretoria do CIn, isso é uma decisão grande demais para ficar implícita.

Minha contribuição aqui é explicitar uma questão anterior à compra das GPUs: **como o serviço absorve pico, contingência e crescimento?** Em um ambiente universitário, isso muda tanto o capex inicial quanto a governança operacional.

## Contribuições incorporadas à caixa
- **Novo parâmetro**: `Estratégia de provisão de capacidade` (`morphology/params/12-provisao.yaml`) com três posições:
  - `opt.provisao.local`
  - `opt.provisao.apuana`
  - `opt.provisao.cloud_burst`
- **Novos critérios qualitativos** em `morphology/criteria.yaml`:
  - `prazo_implantacao`
  - `elasticidade`
- **Novas restrições fracas** em `morphology/constraints.yaml`, para registrar riscos de:
  - `Apuana × chat interativo`
  - `Apuana × política aberta com cota`
  - `cloud burst × política aberta com cota`
- **Novos argumentos** pró/contra em `morphology/arguments.yaml` para manter a divergência explícita, não escondida.

## Tese proposta para debate
O cluster local não precisa carregar sozinho o pico de demanda desde o primeiro dia.

Há pelo menos três caminhos de provisão que merecem status de opção de primeira classe:

1. **100% local**: mais soberano e previsível, porém com maior capex de entrada e expansão mais lenta.
2. **Local + federação com o Apuana**: aproveita ativos institucionais já existentes para overflow ou filas não interativas, mas precisa respeitar que o Apuana é, por natureza, um ambiente batch.
3. **Local + cloud burst contratual**: reduz a pressão de sobredimensionar o cluster inicial, mas transforma parte do problema em governança de opex, cotas e lock-in.

Minha posição, em modo **divergir**, é que o repositório não deve mais tratar o caminho `100% local` como default implícito. Ele deve disputar explicitamente com `federar` e `burst`.

## Evidências externas usadas nesta contribuição
- A documentação oficial do **Slurm** afirma que recursos em provedores de nuvem podem ser combinados com um cluster existente para processar carga excedente (*cloud bursting*) ou operar como cluster independente.
- A documentação oficial do **Slurm Federation** descreve federação de clusters com agendamento *peer-to-peer*, em que jobs submetidos ao cluster de origem são replicados e disputados entre clusters membros.
- A página oficial da **AWS EC2 P5** mostra que instâncias com **H100** e **H200** estão disponíveis hoje como recurso consumível por demanda e integráveis a **AWS Batch** e **ParallelCluster**, o que torna `cloud burst` uma opção operacional real, não hipotética.

## Limite importante desta proposta
Esta contribuição **não defende** mover o serviço principal para nuvem, nem assumir que o Apuana consegue atender bem requisições interativas. Pelo contrário: as restrições adicionadas registram exatamente esses riscos. O objetivo aqui é **abrir a decisão correta**, não fechá-la cedo demais.

## Perguntas abertas que eu deixo para os próximos ciclos
- O Apuana aceitaria overflow de inferência apenas para filas assíncronas, ou haveria espaço para alguma integração com workloads quase interativos?
- O orçamento do CIn tolera uma parcela pequena e explícita de **opex variável** para contingência, ou a exigência é capex quase totalmente fechado?
- A camada de serving/gateway deveria distinguir, desde o início, requisições **interativas** de requisições **assíncronas/lote**, para permitir provisão híbrida sem degradar UX?
- Vale introduzir, em ciclo futuro, um critério quantitativo de **opex anual** separado da conta mensal de energia local?
