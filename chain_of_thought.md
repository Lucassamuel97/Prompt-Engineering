[⬅️ Voltar para o README](./README.md)

# Chain of Thought (CoT)

Chain of Thought (CoT) é uma técnica de engenharia de prompt que instrui o modelo a externalizar seu raciocínio passo a passo, permitindo que ele resolva tarefas que exigem lógica, múltiplas etapas ou operações intermediárias. Em vez de apenas fornecer a resposta final, o modelo mostra seu processo de pensamento.

## Estudo

A técnica foi formalizada no artigo ["Chain-of-Thought Prompting Elicits Reasoning in Large Language Models"](https://arxiv.org/abs/2201.11903) de Wei et al. (2022), demonstrando que grandes modelos como PaLM e GPT-3 apresentam desempenho significativamente superior em tarefas de raciocínio lógico e aritmético quando induzidos a pensar de forma encadeada.

## Advanced Reasoning

O CoT é a base para os recursos de Advanced Reasoning em LLMs, como GPT-4, Claude e Gemini. Esses modelos foram treinados com instruções e exemplos que incentivam raciocínio multietapas, explicações lógicas e reflexões auditáveis.

Chain of Thought permite que o modelo não apenas chegue à resposta, mas também demonstre como chegou até ela, oferecendo transparência, confiabilidade e contexto técnico.

## Quando utilizar

- Diagnostico de falahas de bugs
- Planejamento lógico de processos
- Argumentações comparativas entre abordagens

## Vantagens

- **Raciocínio explícito:** permite que o modelo demonstre seu processo de pensamento passo a passo.
- **Maior resolução de problemas complexos:** melhora significativamente o desempenho em tarefas que exigem múltiplas etapas de raciocínio.
- **Transparência e auditabilidade:** torna o processo decisório do modelo visível, facilitando a verificação da lógica utilizada.

## Limitações

- Gera saídas mais longas, o que pode ser custoso em prompts com limite de tokens.
- Pode introduzir ruído se o modelo gerar cadeias de pensamento incorretas.
- Requer modelo suficientemente treinado para compreender e aplicar o passo a passo com qualidade.
- Se não combinado com critérios de parada, pode prolongar desnecessariamente o raciocínio.
  - "Pense passo a passo até chegar a uma conclusão única e final."
  - "Pare quando tiver certeza da resposta."
  - "Após concluir as etapas, retorne apenas a resposta final."

# Estrutura e exemplos

Você é um engenheiro de software com 20 anos de experiência em sistemas concorrentes e distribuídos. Seu trabalho é revisar o código a seguir e identificar falhas ou melhorias. Pense passo a passo, justificando cada ponto com base nas práticas recomendadas em Go. Ao final, revise a sequência de etapas e forneça uma conclusão objetiva.

Use a seguinte estrutura:

Etapa 1: <descrição>
Etapa 2: <descrição> ...
Resultado final: <conclusão>

# Debugging com raciocínio lógico

**Prompt:**

Você é um desenvolvedor Go. Analise o seguinte código e explique, passo a passo, por que ele pode causar um erro:

```go
var lista []string
fmt.Println(lista[0])
```

**Resposta esperada:**

Etapa 1: A variável `lista` é declarada como slice de strings, mas não foi inicializada.

Etapa 2: Um slice não inicializado tem tamanho zero (`len(lista) == 0`).

Etapa 3: Acessar `lista[0]` viola o limite do slice, pois não há elementos.

Resultado final: o programa entra em pânico (`panic`) por acesso fora dos limites.

### Planejamento básico

**Prompt:**

Descreva todas as etapas envolvidas na migração de uma aplicação monolítica para microsserviços baseados em eventos. Para cada etapa, inclua pré-requisitos, riscos e validações. Organize o raciocínio em sequência lógica e valide antes de concluir.

**Resposta esperada:**

Etapa 1: Identificação dos domínios de negócio.

- Pré-requisitos: Conhecimento profundo dos processos de negócio.
- Riscos: Subdivisão inadequada pode gerar dependências ocultas.
- Validação: Revisão com especialistas de domínio.

Etapa 2: Definição de fronteiras de contexto (bounded contexts).

- Pré-requisitos: Mapear interações e dependências entre domínios.
- Riscos: Fronteiras mal definidas levam a acoplamento excessivo.
- Validação: Diagramas de contexto revisados por arquitetos.

Etapa 3: Extração de serviços mais isolados com menor acoplamento.

- Pré-requisitos: Identificação de módulos independentes.
- Riscos: Quebra de funcionalidades críticas ou dependências não mapeadas.
- Validação: Testes de integração e revisão de dependências.

Etapa 4: Implementação de mensageria (ex: RabbitMQ) com fallback e DLQs.

- Pré-requisitos: Definição dos eventos e contratos de mensagens.
- Riscos: Perda de mensagens, duplicidade ou falhas de entrega.
- Validação: Testes de resiliência e simulação de falhas.

Etapa 5: Implementação de observabilidade: logs, métricas e tracing.

- Pré-requisitos: Ferramentas de monitoramento integradas.
- Riscos: Falta de visibilidade sobre falhas distribuídas.
- Validação: Dashboards e alertas validados em ambiente de testes.

Resultado final: Sequência validada de etapas para migração segura e auditável de monólito para microsserviços baseados em eventos.

## Estratégias inspiradas na Anthropic Prompt Library

- **Persona + Objetivo + Estrutura clara:** contextualiza a função do modelo e define o tom da resposta.
- **Chamado à reflexão lógica:** "Pense passo a passo", "Justifique cada etapa".
- **Formato de saída padronizado:** etapas numeradas + conclusão objetiva.
- **Autoavaliação embutida:** "Verifique se todos os passos estão consistentes".
- **Critério de parada lógico:** encerrar ao atingir o raciocínio final.

## Técnicas avançadas de CoT com delimitações estruturais (Anthropic-style)

Modelos como Claude e GPT respondem melhor quando o prompt apresenta **delimitações estruturais explícitas**. Uma técnica bastante utilizada pela Anthropic, segundo sua própria Claude Prompt Library, é o uso de **delimitadores XML-like** como `<thought>`, `<reasoning>`, `<answer>`, etc., para **separar raciocínio da resposta final**, melhorar a legibilidade, e tornar o prompt mais auditável.

## Principais marcadores XML-like (Anthropic-style)

Aqui estão alguns dos principais marcadores XML-like comumente usados, especialmente no estilo inspirado pela Anthropic:

### `<thinking> ... </thinking>`

**Propósito:** Delimita a seção onde o modelo articula seu processo de raciocínio, passo a passo, antes de chegar à conclusão.

**Exemplo:**

```xml
<thinking>
Primeiro, preciso identificar as principais entidades na pergunta.
Depois, preciso entender a relação entre elas.
Em seguida, vou buscar informações relevantes sobre cada entidade.
Finalmente, vou combinar as informações para formular a resposta.
</thinking>
```

---

### `<scratchpad> ... </scratchpad>` ou `<internal_monologue> ... </internal_monologue>`

**Propósito:** Usados para registrar pensamentos intermediários, cálculos ou rascunhos internos que ajudam a processar a informação. A escolha entre eles depende da nuance desejada ("rascunho" vs. "monólogo interno").

**Exemplo:**

```xml
<scratchpad>
A pergunta é sobre X e Y.
X = 5, Y = 10.
A operação é adição.
5 + 10 = 15.
</scratchpad>
```

---

### `<problem> ... </problem>` ou `<question> ... </question>`

**Propósito:** Delimita a pergunta ou o problema original que o modelo precisa resolver, mantendo o foco e a clareza.

**Exemplo:**

```xml
<question>
Qual é a capital da França e qual é a sua população aproximada?
</question>
```

---

### `<plan> ... </plan>`

**Propósito:** Permite ao modelo delinear um plano de ação antes de executar as etapas de pensamento.

**Exemplo:**

```xml
<plan>
1. Identificar a capital da França.
2. Pesquisar a população da capital identificada.
3. Formular a resposta final.
</plan>
```

---

### `<step> ... </step>` ou `<instruction> ... </instruction>`

**Propósito:** Decompõe o processo de pensamento em etapas ou instruções individuais e explícitas. Frequentemente usado dentro de `<thinking>` ou `<plan>`.

**Exemplo:**

```xml
<thinking>
        <step>Primeiro, vou analisar a primeira parte da pergunta: "Qual é a capital da França?".</step>
        <step>Lembro que a capital da França é Paris.</step>
        <step>Agora, vou analisar a segunda parte: "qual é a sua população aproximada?".</step>
        <step>Vou precisar de uma fonte confiável para essa informação.</step>
</thinking>
```

---

### `<context> ... </context>`

**Propósito:** Fornece informações contextuais relevantes que o modelo deve considerar ao formular sua resposta.

**Exemplo:**

```xml
<context>
Artigo sobre a economia da França em 2023.
O usuário está perguntando sobre tendências de crescimento.
</context>
```

---

### `<response> ... </response>`, `<answer> ... </answer>` ou `<final_answer> ... </final_answer>`

**Propósito:** Delimita a resposta final do modelo, após o processo de Chain of Thought.

**Exemplo:**

```xml
<thinking>
A capital da França é Paris.
De acordo com dados recentes, a população de Paris é de aproximadamente 2.1 milhões de habitantes na cidade propriamente dita, e mais de 11 milhões na área metropolitana.
</thinking>
<answer>
A capital da França é Paris, e sua população aproximada é de 2.1 milhões de habitantes na cidade e mais de 11 milhões na área metropolitana.
</answer>
```

# Motivação para usar marcadores estruturais

- Reduz ambiguidade entre raciocínio e resposta.
- Permite que o modelo organize suas ideias de maneira hierárquica.
- Facilita análises posteriores do output por humanos ou outros sistemas.
- Ajuda o modelo a se manter dentro de um fluxo lógico, sem saltos.

# Exemplo

## Prompt:

Você é um engenheiro de software especialista em arquitetura de sistemas web. Sua tarefa é pensar passo a passo sobre os requisitos técnicos para construir um backend de uma aplicação de Todo List colaborativa com autenticação de usuários, categorias personalizáveis e suporte a tarefas compartilhadas entre times.

Escreva seu raciocínio entre `<thought>` e o resumo técnico final entre `<answer>`. Use também `<steps>` para dividir o pensamento por área de responsabilidade.

## Resposta esperada:

```xml
<thought>
<steps>
        <step>1. Autenticação de Usuários: O backend deve implementar autenticação segura, preferencialmente via JWT ou OAuth2, para garantir que apenas usuários autorizados acessem e modifiquem dados.</step>
        <step>2. Modelagem de Usuários e Times: É necessário definir entidades para usuários e times, permitindo que usuários pertençam a múltiplos times e que tarefas possam ser atribuídas a times ou indivíduos.</step>
        <step>3. Categorias Personalizáveis: O sistema deve permitir que cada usuário ou time crie, edite e remova categorias para organizar tarefas conforme suas necessidades.</step>
        <step>4. Compartilhamento de Tarefas: As tarefas devem suportar múltiplos responsáveis e permissões de acesso, possibilitando colaboração entre membros do time.</step>
        <step>5. Controle de Permissões: Implementar regras para garantir que apenas usuários autorizados possam editar, visualizar ou excluir tarefas e categorias compartilhadas.</step>
        <step>6. API RESTful: Expor endpoints claros para operações de CRUD em tarefas, categorias, usuários e times, seguindo boas práticas de versionamento e documentação.</step>
        <step>7. Persistência de Dados: Utilizar banco de dados relacional (ex: PostgreSQL) para garantir integridade referencial entre usuários, times, tarefas e categorias.</step>
        <step>8. Sincronização e Conflitos: Considerar mecanismos de controle de concorrência para evitar conflitos em edições simultâneas de tarefas compartilhadas.</step>
        <step>9. Observabilidade e Logs: Incluir logging estruturado e métricas para monitorar operações críticas e facilitar troubleshooting.</step>
</steps>
</thought>
<answer>
O backend deve oferecer autenticação robusta, modelagem flexível de usuários e times, suporte a categorias customizáveis e tarefas compartilhadas, controle granular de permissões, endpoints RESTful bem definidos, persistência consistente dos dados e mecanismos para lidar com concorrência e observabilidade. Isso garante colaboração eficiente, segurança e escalabilidade para a aplicação de Todo List colaborativa.
</answer>
```


# Comparativo

| Tipo de Prompt      | Requer Exemplos | Gera Raciocínio | Ideal para                               |
| :------------------ | :-------------- | :-------------- | :--------------------------------------- |
| Zero-Shot           | Nenhum          | Média           | Baixo                                    |
| One-Shot / Few-Shot | Sim             | Opcional        | Imitar formato, estilo ou padrões        |
| Chain of Thought    | Indiferente     | Sim             | Lógica, planejamento, análise, debugging |