[⬅️ Voltar para o README](./README.md)

# Zero-shot Prompting

## 📖 Descrição

Zero-shot prompting é a técnica de solicitar que o modelo realize uma tarefa **sem fornecer exemplos** anteriores, apenas com uma **instrução clara em linguagem natural**.

---

## 🔬 Fundamento

- Baseado no conceito de **Zero-shot learning** de Machine Learning.
- O modelo utiliza apenas o conhecimento adquirido durante o treinamento para executar a tarefa.
- Popularizado pelo paper **"Language Models are Few-Shot Learners" (GPT-3, 2020)**.

---

## 🚀 Quando Utilizar

✔️ **Ideal para:**

- Tarefas simples e objetivas (tradução, resumo, definição, perguntas diretas).
- Obter respostas rápidas sem configurações complexas.

## ⚠️ Limitações

- Pode falhar em tarefas mais complexas ou menos frequentes para o modelo.
- Não oferece controle sobre o formato da resposta.
- Dependente da compreensão implícita do modelo sobre a tarefa.
- **Alucinação de respostas:** o modelo pode gerar conteúdo incorreto com alta confiança.
- Variação com pequenas mudanças na formatação: prompts semanticamente equivalentes podem gerar resultados diferentes.
- Dificuldade em tarefas de raciocínio lógico, análises comparativas ou inferência do contexto factual.

---

## 🛠️ Estratégias de Mitigação

Mesmo mantendo a proposta de **não fornecer exemplos**, algumas práticas ajudam a melhorar os resultados com Zero-shot Prompting:

### 🔹 Especificidade

Instruções claras, que detalham o que se espera, aumentam a precisão.

- **❌ Exemplo ruim:**  
  `“Analise esse código.”`

- **✅ Melhorado:**  
  `“Explique o que esse código Go faz e liste possíveis problemas de performance.”`

---

### 🔹 Linguagem declarativa e orientada à tarefa

Preferência por comandos diretos a perguntas abertas.

- **Exemplo:**  
  `“Liste os principais motivos para erros de memória em linguagem Go.”`

---

### 🔹 Sinalização do formato esperado

Indicar o formato desejado da saída ajuda a obter respostas mais precisas e estruturadas.

- **Exemplo:**  
  `“Responda em forma de tópicos” ou “Escreva uma explicação de 3 parágrafos”`

---

## 🎯 In-Context Instruction Learning

Mesmo sem exemplos, prompts estruturados com clareza (**persona, formato, objetivo**) ajudam o modelo a responder melhor.

Instruções mais detalhadas **melhoram significativamente a performance zero-shot**.

### 📝 Exemplo de melhoria:

- **Antes:**  
  `“Explique o que é uma goroutine.”`

- **Depois:**  
  `“Você é um especialista em Go. Escreva dois parágrafos explicando o que é uma goroutine, como ela é usada e quais são suas limitações. Seja claro, técnico e direto.”`

---

## 💡 Boas Práticas da Microsoft para Zero-Shot Prompting

- ✅ **Especificar o papel do modelo:**  
  `"Você é um especialista em..."`

- ✅ **Especificar a saída desejada:**  
  `"Responda em tópicos"` ou `"Formato JSON"`

- ✅ **Garantir que o modelo compreenda a meta:**  
  `"Seu objetivo é..."`

### 🔍 Exemplo completo:  
`"Você é um consultor técnico. Seu trabalho é analisar este trecho de código e sugerir melhorias de performance. Responda em tópicos e justifique cada sugestão."`

## 📚 Referência

📄 Paper: [Language Models are Few-Shot Learners](https://arxiv.org/abs/2005.14165) https://arxiv.org/abs/2005.14165

🔗 [Prompt Engineering with Azure OpenAI Service (Microsoft Learn)](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/prompt-engineering)

---
