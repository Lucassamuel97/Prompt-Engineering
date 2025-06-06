# 🧠 Variações Avançadas de Prompts (Prompt Engineering)

Este documento apresenta as principais variações avançadas de prompts utilizadas em **Prompt Engineering**, a prática de projetar instruções otimizadas para interagir com modelos de inteligência artificial generativa.

---

## Prompts comumente utilizados 

| Nome                         | Descrição                                                                 | Exemplo                                                         |
|------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------------|
| [Zero-shot Prompting](zero_shot_prompting.md)     | A IA recebe apenas a tarefa, sem exemplos.                               | `Traduza para inglês: 'Eu gosto de café'.`                     |
| [One-shot prompting](one-shot-few-shot.md)      | Fornece **um exemplo** antes da tarefa.                                  | `'Olá' → 'Hello'. Traduza: 'Bom dia' →`                        |
| [Few-shot prompting](one-shot-few-shot.md)       | Fornece **poucos exemplos (2-5)** para orientar o modelo.                | `'Olá' → 'Hello', 'Boa noite' → 'Good night'. Traduza: 'Eu amo aprender' →` |

---
## Prompts Elaborados 
| Nome                         | Descrição                                                                 | Exemplo                                                         |
|------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------------|
| [Chain of Thought (CoT)](chain_of_thought.md) | A IA gera uma **sequência de raciocínio passo a passo** antes da resposta final. | `Para resolver 2 + 2, primeiro pense: 2 + 2 é igual a 4.`      |
| [Skeleton of Thought (SoT)](skeleton_of_thought.md) | O modelo primeiro gera uma estrutura esquelética (um roteiro, tópicos ou plano) antes de gerar a resposta completa.       | `"Primeiro, gere os tópicos principais de um artigo sobre mudança climática. Depois, desenvolva cada tópico em parágrafos."`|
| [Tree-of-thought (ToT)](tree_of_thought.md) | A IA explora diferentes caminhos de raciocínio em formato de árvore, escolhendo os melhores. | `Liste várias formas de resolver esse problema e selecione a mais eficiente.` |
| [Self-consistency prompting](self_consistency.md) | A IA gera várias respostas e escolhe a mais comum ou consistente. | `Responda a pergunta 3 vezes e escolha a resposta mais frequente.` |
| [Directional Stimulus](directional_stimulus.md) | A IA é guiada por comandos ou estímulos que direcionam seu raciocínio. | `Responda como um especialista em segurança cibernética.` |
| **Reflexive prompting (Self-reflection)** | Pede que a IA **avalie, critique ou melhore sua própria resposta.** | `Releia sua resposta anterior e sugira melhorias.`             |
| **Multimodal prompting**     | Usa múltiplos tipos de entrada, como texto, imagem, áudio, vídeo.        | `Descreva essa imagem e sugira uma legenda criativa.`          |
| **Dynamic prompting**        | O prompt é gerado dinamicamente, com base em dados, contexto ou histórico. | *(Usado em APIs e aplicações dinâmicas.)*                      |
| **ReAct prompting**          | Combina **raciocínio (Reasoning)** com **ação (Action)**, permitindo que a IA pense, execute e continue iterando. | `Pense: o que falta? Aja: busque no banco de dados. Continue.` |

---

## Resumo comparativo: CoT, SoT, ToT

| Técnica                | Situação ideal                         | Justificativa                               | Exemplo de prompt                                                                                                                                                                                             |
| :--------------------- | :------------------------------------- | :------------------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Chain of Thought (CoT) | Explicar bugs                          | Raciocínio encadeado com lógica explicada   | "Explique passo a passo por que o código abaixo pode gerar um panic em Go. Analise como um engenheiro faria debug em produção."                                                                           |
| Skeleton of Thought (SoT)| Especificar módulos com seções fixas | Exige consistência e organização por tópicos | "Crie uma especificação técnica para um módulo de autenticação JWT usando os seguintes tópicos: requisitos funcionais, modelo de dados, fluxos, validações, segurança e integração."                           |
| Tree of Thought (ToT)  | Comparar opções (ex: cache)            | Exploração de alternativas e decisão justificada | "Considere três formas de aplicar cache em um sistema web: in-memory, Redis e CDN. Para cada uma, descreva a estratégia, vantagens, desvantagens e cenário ideal de uso. Ao final, selecione a melhor com base em latência, custo e simplicidade." |
| SoT + CoT      | Planejamento de arquitetura     | Organização por tópicos com raciocínio detalhado | "Estruture a arquitetura de um sistema de Todo List com autenticação, API REST e persistência. Responda por tópicos: visão geral, autenticação, banco de dados, fluxos principais, escalabilidade. Em cada tópico, pense passo a passo como um arquiteto de software."                                            |
| ToT + SoT + CoT | Definir melhor stack tecnológica | Estrutura, múltiplas alternativas e raciocínio interno | "Compare as stacks Go, Node.js e Python para microserviços. Para cada uma, siga os tópicos: performance, ecossistema, produtividade, complexidade de deploy e casos de uso recomendados. Dentro de cada tópico, pense passo a passo. Ao final, recomende a stack ideal para um sistema com 10 microsserviços interconectados." |
| ToT + SoT | Comparação de bancos de dados | Análise comparativa organizada por critérios | "Compare os tipos de banco de dados SQL, NoSQL e NewSQL para uma aplicação de leitura intensiva. Para cada um, responda usando os tópicos: modelo de dados, escalabilidade, latência, consistência e custo operacional. Ao final, indique qual abordagem é mais indicada para esse cenário." |

### Casos de uso abordados

| Técnica aplicada     | Situação                                                    | Justificativa                                                 |
| :------------------- | :---------------------------------------------------------- | :------------------------------------------------------------ |
| Chain of Thought (CoT) | Explicar por que um bug ocorre                              | Precisa de raciocínio encadeado com lógica explicada        |
| Skeleton of Thought (SoT)| Especificar um módulo de autenticação com seções fixas    | Exige consistência e organização por tópicos                 |
| Tree of Thought (ToT)  | Comparar 3 formas de aplicar cache (in-memory, Redis, CDN) | Exige exploração de alternativas e decisão final justificada  |
| SoT + CoT            | Planejar arquitetura de um sistema com API, banco e autenticação | Exige estrutura e raciocínio técnico dentro de cada seção   |
| ToT + SoT + CoT      | Definir melhor stack entre Go, Node.js e Python para microserviços | Requer estrutura, múltiplas alternativas e raciocínio interno completo |
| ToT + SoT            | Comparar bancos SQL, NoSQL e NewSQL para leitura intensiva   | Múltiplas estratégias com análise técnica estruturada, sem exigir CoT |

### Conclusão

Cada técnica possui forças complementares:

* **CoT** → Raciocínio lógico.
* **SoT** → Organização e completude.
* **ToT** → Comparação e tomada de decisão.
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