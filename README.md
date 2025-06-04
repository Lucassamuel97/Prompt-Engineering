# 🧠 Variações Avançadas de Prompts (Prompt Engineering)

Este documento apresenta as principais variações avançadas de prompts utilizadas em **Prompt Engineering**, a prática de projetar instruções otimizadas para interagir com modelos de inteligência artificial generativa.

---

## Prompts comumente utilizados 

| Nome                         | Descrição                                                                 | Exemplo                                                         |
|------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------------|
| [Zero-shot Prompting](zero_shot_prompting.md)     | A IA recebe apenas a tarefa, sem exemplos.                               | `Traduza para inglês: 'Eu gosto de café'.`                     |
| [One-shot prompting](one-shot-few-shot.md)      | Fornece **um exemplo** antes da tarefa.                                  | `'Olá' → 'Hello'. Traduza: 'Bom dia' →`                        |
| [Few-shot prompting](one-shot-few-shot.md)       | Fornece **poucos exemplos (2-5)** para orientar o modelo.                | `'Olá' → 'Hello', 'Boa noite' → 'Good night'. Traduza: 'Eu amo aprender' →` |

### Comparativo

| Tipo de Prompt | Exemplos | Precisão | Controle de Saída | Custo |
|----------------|----------|----------|-------------------|-------|
| Zero-Shot      | Nenhum   | Média    | Baixo             | Baixo |
| One-Shot       | 1        | Média+   | Médio             | Médio |
| Few-Shot       | 2-5      | Alta     | Alto              | Alto  |

---
## Prompts Elaborados 
| Nome                         | Descrição                                                                 | Exemplo                                                         |
|------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------------|
| [Chain-of-thought prompting](chain_of_thought.md) | Estimula a IA a pensar em etapas antes da resposta final.               | `Explique passo a passo como calcular 124 x 36 mentalmente.`   |
| **Self-consistency prompting** | Usa várias execuções com chain-of-thought e escolhe a mais comum.       | *(Executado internamente — roda múltiplas vezes e seleciona a resposta mais frequente.)* |
| **Reflexive prompting (Self-reflection)** | Pede que a IA **avalie, critique ou melhore sua própria resposta.** | `Releia sua resposta anterior e sugira melhorias.`             |
| **Tree-of-thought prompting** | A IA explora diferentes caminhos de raciocínio em formato de árvore, escolhendo os melhores. | `Liste várias formas de resolver esse problema e selecione a mais eficiente.` |
| **Multimodal prompting**     | Usa múltiplos tipos de entrada, como texto, imagem, áudio, vídeo.        | `Descreva essa imagem e sugira uma legenda criativa.`          |
| **Dynamic prompting**        | O prompt é gerado dinamicamente, com base em dados, contexto ou histórico. | *(Usado em APIs e aplicações dinâmicas.)*                      |
| **ReAct prompting**          | Combina **raciocínio (Reasoning)** com **ação (Action)**, permitindo que a IA pense, execute e continue iterando. | `Pense: o que falta? Aja: busque no banco de dados. Continue.` |

---

## Resumo Visual Rápido

```markdown
| 🏷️ Prompt             | 📝 Resumo Visual                                  |
|-----------------------|---------------------------------------------------|
| Zero-shot             | Só a tarefa                                       |
| One-shot              | 1 exemplo                                         |
| Few-shot              | Alguns exemplos                                   |
| Chain-of-thought      | Pense passo a passo                               |
| Self-consistency      | Escolhe a resposta mais comum de vários pensamentos|
| Reflexive             | IA revisa sua própria resposta                    |
| Tree-of-thought       | Explora vários caminhos e escolhe o melhor        |
| Multimodal            | Texto + imagem + áudio + vídeo                    |
| Dynamic               | Prompts gerados dinamicamente no contexto         |
| ReAct                 | IA pensa, executa ações, volta a pensar (ciclo)   |
```

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