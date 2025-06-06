[⬅️ Voltar para o README](./README.md)

# Self-Consistency

## Como funciona a técnica

- O prompt induz o modelo a pensar passo a passo (*Chain of Thought*).
- A tarefa é executada diversas vezes (tipicamente de 5 a 10).
- As respostas geradas são coletadas e comparadas.
- A saída final é definida por votação majoritária ou métrica de consistência.
- O princípio é simples: o modelo pode cometer erros em uma cadeia específica, mas, com múltiplas execuções, as respostas mais confiáveis tendem a convergir.

## Quando utilizar

- Quando há ambiguidade matemática ou estrutural.
- Se a tarefa é suscetível a variações de raciocínio.
- Quando o modelo tende a dar boas respostas às vezes, mas não sempre.
- Para aumentar a confiabilidade da saída com pouco custo computacional adicional.

## Por que funciona

LLMs operam com amostragem probabilística (ex: temperatura > 0), o que os torna suscetíveis a gerar variações, desvios ou respostas inconsistentes. Ao gerar múltiplas execuções:

- Reduzimos alucinações isoladas.
- Aumentamos a chance de obter uma resposta estatisticamente sólida.
- Priorizamos coerência entre caminhos lógicos distintos.

## Referência

- [Self-Consistency: A Simple Way to Improve Language Models](https://arxiv.org/abs/2203.11171)

## Exemplo de situação

Você está desenvolvendo a estimativa de custo mensal para uma aplicação em produção na AWS. A aplicação utiliza:

- 10 instâncias EC2 t3.large (região US East)
- 1 TB de armazenamento EBS
- 1 Load Balancer
- 100 GB de transferência de dados saindo por mês

Como pequenos desvios podem ocorrer entre execuções, você decide aplicar Self-Consistency para gerar múltiplas estimativas e selecionar a mais confiável.

**Prompt (com CoT):**

```markdown
Calcule o custo total mensal dessa infraestrutura. Pense passo a passo.
```

**Execuções (resumidas):**

- **Execução 1**
    - EC2: 10 x $0.0832 x 730h = $607.36
    - EBS: 1024 GB x $0.10 = $102.40
    - ELB: $18.00
    - Data transfer: 100 GB x $0.09 = $9.00
    - **Total:** $736.76

- **Execução 2**
    - EC2: $605.00 (aproximado)
    - EBS: $100.00
    - ELB: $18
    - Transferência: $9
    - **Total:** $732.00

- **Execução 3**
    - EC2: 10 x 0.0832 x 730 = $607.36
    - EBS: 1TB x 0.10 = $102.40
    - Load Balancer: $18
    - Data Out: $9
    - **Total:** $736.76

## Resultado da Self-Consistency

A estimativa de **$736.76** foi obtida em duas execuções, ambas apresentando cálculos detalhados e consistentes. Por sua frequência e exatidão, essa resposta é considerada a mais confiável.

**Resposta selecionada:**  
$736.76 — confirmada como mais precisa e recorrente entre as múltiplas cadeias de raciocínio.

## Aplicações práticas em engenharia de software

- Estimativas de custo e capacidade (cloud, infraestrutura, armazenamento)
- Planejamento de sizing de ambientes
- Validação de resultados numéricos ou previsões algorítmicas
- Verificação de hipóteses técnicas sob múltiplos critérios
- Comparações de lógica interna em testes de arquitetura

## Dicas de aplicação

- Gere de 5 a 10 respostas com temperatura > 0.5 para estimular caminhos diversos.
- Normalize o formato da saída antes de comparar.
- Pode ser usada manualmente (humano escolhe) ou automaticamente (via votação).


## Exemplo completo usando todas as dicas de aplicação

Você quer estimar o número ideal de shards para uma base de dados multitenant com **80.000 clientes**.

**Prompt:**

```markdown
Qual o número ideal de shards para particionar uma base de dados com 80.000 clientes, considerando escalabilidade, performance e isolamento? Pense passo a passo.
```

**Aplicação prática das dicas:**

- **Temperatura variada (diversidade de raciocínio):**  
    Gere 8 respostas com temperaturas entre 0.6 e 0.8 para explorar diferentes caminhos de raciocínio.

- **Normalização da saída:**  
    Antes de comparar, converta variações como:
    - `"~10 shards"`, `"10"`, `"dez"` → **"10"**
    - Formatação monetária ou numérica (ex: `R$10k` → `10000`)

- **Seleção da resposta final:**  
    - 5 das 8 execuções sugerem **10 shards**, justificando com argumentos como:
        - "8000 clientes por shard"
        - "balanceamento operacional"
        - "flexibilidade para crescimento futuro"
    - Um script simples conta a frequência das respostas e seleciona a mais recorrente.

**Resultado final:**  
**10 shards** — justificado por frequência, coerência técnica e compatibilidade com os critérios operacionais do sistema.
