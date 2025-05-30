# 🧠 Variações Avançadas de Prompts (Prompt Engineering)

Este documento apresenta as principais variações avançadas de prompts utilizadas em **Prompt Engineering**, a prática de projetar instruções otimizadas para interagir com modelos de inteligência artificial generativa.

---

## Variações Avançadas

| Nome                         | Descrição                                                                 | Exemplo                                                         |
|------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------------|
| **Zero-shot prompting**      | A IA recebe apenas a tarefa, sem exemplos.                               | `Traduza para inglês: 'Eu gosto de café'.`                     |
| **One-shot prompting**       | Fornece **um exemplo** antes da tarefa.                                  | `'Olá' → 'Hello'. Traduza: 'Bom dia' →`                        |
| **Few-shot prompting**       | Fornece **poucos exemplos (2-5)** para orientar o modelo.                | `'Olá' → 'Hello', 'Boa noite' → 'Good night'. Traduza: 'Eu amo aprender' →` |
| **Chain-of-thought prompting** | Estimula a IA a pensar em etapas antes da resposta final.               | `Explique passo a passo como calcular 124 x 36 mentalmente.`   |
| **Self-consistency prompting** | Usa várias execuções com chain-of-thought e escolhe a mais comum.       | *(Executado internamente — roda múltiplas vezes e seleciona a resposta mais frequente.)* |
| **Reflexive prompting (Self-reflection)** | Pede que a IA **avalie, critique ou melhore sua própria resposta.** | `Releia sua resposta anterior e sugira melhorias.`             |
| **Tree-of-thought prompting** | A IA explora diferentes caminhos de raciocínio em formato de árvore, escolhendo os melhores. | `Liste várias formas de resolver esse problema e selecione a mais eficiente.` |
| **Multimodal prompting**     | Usa múltiplos tipos de entrada, como texto, imagem, áudio, vídeo.        | `Descreva essa imagem e sugira uma legenda criativa.`          |
| **Dynamic prompting**        | O prompt é gerado dinamicamente, com base em dados, contexto ou histórico. | *(Usado em APIs e aplicações dinâmicas.)*                      |
| **ReAct prompting**          | Combina **raciocínio (Reasoning)** com **ação (Action)**, permitindo que a IA pense, execute e continue iterando. | `Pense: o que falta? Aja: busque no banco de dados. Continue.` |

---

## Resumo Visual Rápido

Zero-shot → Só a tarefa
One-shot → 1 exemplo
Few-shot → Alguns exemplos
Chain-of-thought → Pense passo a passo
Self-consistency → Escolhe a resposta mais comum de vários pensamentos
Reflexive → IA revisa sua própria resposta
Tree-of-thought → Explora vários caminhos e escolhe o melhor
Multimodal → Texto + imagem + áudio + vídeo
Dynamic → Prompts gerados dinamicamente no contexto
ReAct → IA pensa, executa ações, volta a pensar (ciclo)

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

⚠️ **Limitações:**
- Menor precisão em tarefas complexas ou sensíveis.
- Pouco controle sobre tom, estilo ou formato específico da saída.

---

## 📦 Exemplos
Crie uma função em Python que calcule o fatorial de um número.
```bash
➡️ 
```python
def fatorial(n):
    if n == 0:
        return 1
    else:
        return n * fatorial(n-1)

```
---

## 📚 Referência  
📄 Paper: [Language Models are Few-Shot Learners](https://arxiv.org/abs/2005.14165) https://arxiv.org/abs/2005.14165

---



## 📚 Referências e Leitura Recomendada

- [OpenAI Cookbook](https://github.com/openai/openai-cookbook)
- Papers:
  - **Chain of Thought Prompting Elicits Reasoning in Large Language Models** ([arXiv](https://arxiv.org/abs/2201.11903))
  - **ReAct: Synergizing Reasoning and Acting in Language Models** ([arXiv](https://arxiv.org/abs/2210.03629))
  - **Tree of Thoughts: Deliberate Problem Solving with Large Language Models** ([arXiv](https://arxiv.org/abs/2305.10601))

---

## ✨ Sobre

Este repositório tem como objetivo documentar variações avançadas de engenharia de prompts, servindo como guia de referência para estudos, desenvolvimento de aplicações com IA generativa e melhoria na interação com modelos de linguagem.

---