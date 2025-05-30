[⬅️ Voltar para o README](./README.md)

## 🛠️ One-shot vs. Few-shot Prompting: Um Exemplo Prático

#Nesta seção, vamos ilustrar a diferença e a relação entre One-shot e Few-shot prompting usando um exemplo prático. Lembre-se que **One-shot prompting é um caso específico de Few-shot prompting**, onde exatamente um exemplo é fornecido. O Few-shot prompting, de forma mais geral, refere-se ao uso de um pequeno número de exemplos (tipicamente 2 a 5, mas pode ser mais).

**Tarefa Exemplo:** Classificação de Sentimento de Texto.
O objetivo é que o modelo classifique um texto como "positivo", "negativo" ou "neutro".

---

### 🔹 One-shot Prompting (1 Exemplo)

No One-shot prompting, fornecemos uma instrução clara e **um único exemplo** para guiar o modelo.

**📝 Exemplo de Prompt One-shot:**

```
Classifique o sentimento do seguinte texto como positivo, negativo ou neutro.

Texto exemplo: "Eu realmente não gostei da comida, estava fria e sem sabor."
Sentimento exemplo: negativo

Texto para classificar: "Este filme é absolutamente fantástico, uma obra-prima!"
Sentimento:
```

**Explicação do One-shot:**
O único exemplo ("Eu realmente não gostei da comida..." levando a "negativo") ajuda o modelo a:

Entender o formato de saída esperado (neste caso, uma única palavra indicando o sentimento).
Ter uma referência do tipo de análise de sentimento solicitada.
Inferir que deve aplicar um raciocínio similar ao novo texto.
Este método pode ser suficiente para tarefas onde o conceito é relativamente claro para o modelo e o formato desejado é simples.

### 🔹 Few-shot Prompting (N > 1 Exemplos)

No Few-shot prompting, fornecemos uma instrução clara e múltiplos exemplos. Isso pode ajudar o modelo a entender melhor nuances, diferentes casos de uso, e a generalizar de forma mais robusta.

**📝 Exemplo de Prompt Few-shot (2 Exemplos - Two-shot):**

```
Classifique o sentimento do seguinte texto como positivo, negativo ou neutro.

Texto exemplo 1: "Eu realmente não gostei da comida, estava fria e sem sabor."
Sentimento exemplo 1: negativo

Texto exemplo 2: "O dia está agradável e o parque está lindo, aproveitei cada momento!"
Sentimento exemplo 2: positivo

Texto para classificar: "O relatório é factual e direto ao ponto, sem opiniões."
Sentimento:
```

**📝 Exemplo de Prompt Few-shot (3 Exemplos - Three-shot):**

```
Classifique o sentimento do seguinte texto como positivo, negativo ou neutro.

Texto exemplo 1: "Eu realmente não gostei da comida, estava fria e sem sabor."
Sentimento exemplo 1: negativo

Texto exemplo 2: "O dia está agradável e o parque está lindo, aproveitei cada momento!"
Sentimento exemplo 2: positivo

Texto exemplo 3: "A reunião ocorreu conforme o planejado, sem grandes intercorrências ou novidades."
Sentimento exemplo 3: neutro

Texto para classificar: "Este filme é absolutamente fantástico, uma obra-prima!"
Sentimento:
```

**Explicação do Few-shot (com N>1 exemplos):**

- Com múltiplos exemplos:
  - O modelo observa mais variações da tarefa. No exemplo de 3-shot, ele vê demonstrações para "negativo", "positivo" e "neutro". Isso é particularmente útil se a categoria "neutro", por exemplo, não fosse óbvia apenas com a instrução ou com um único exemplo.
  - Ajuda a obter um formato de saída mais consistente e aderente ao padrão desejado.
  - Aumenta a probabilidade de o modelo capturar a intenção correta, especialmente se a tarefa tiver ambiguidades que um único exemplo não conseguiria resolver completamente.
  - Pode guiar o modelo em tarefas que exigem um raciocínio mais complexo ou distinções sutis entre categorias.

---

### 🔹 Análise Comparativa: One-shot vs. Few-shot

### Semelhanças Fundamentais

- Ambos se baseiam no **aprendizado em contexto** (*in-context learning*): o modelo aprende a realizar a tarefa a partir das demonstrações fornecidas diretamente no prompt, sem necessidade de re-treinamento (*fine-tuning*).
- O objetivo principal é **guiar o modelo para a resposta desejada** em termos de conteúdo, formato, estilo ou tipo de raciocínio.

### Diferença Principal

- **Número de exemplos fornecidos:**
    - **One-shot:** Exatamente 1 exemplo.
    - **Few-shot (N > 1):** Mais de 1 exemplo (geralmente um número pequeno como 2, 3, 5).

### Quando usar One-shot

- Tarefas mais simples e diretas, onde o modelo já tem uma boa compreensão subjacente.
- Quando o formato de saída é fácil de demonstrar com um único exemplo.
- Para economizar tokens no prompt (prompts mais curtos, custos menores e latência reduzida).
- Quando um bom exemplo único é altamente representativo da tarefa.

### Quando usar Few-shot (N > 1)

- Tarefas mais complexas, com nuances ou que exigem raciocínio mais elaborado.
- Para demonstrar diferentes categorias de saída, estilos de resposta ou formatos variados.
- Para aumentar a robustez e a precisão da resposta, especialmente se o One-shot não estiver performando bem.
- Quando o modelo tem dificuldade em generalizar a partir de um único exemplo ou há risco de se fixar em alguma peculiaridade de um único exemplo.

### Considerações Importantes para Ambos

- **Qualidade dos Exemplos:** Exemplos ruins, ambíguos ou inconsistentes levam a resultados ruins, independentemente de serem One-shot ou Few-shot. Os exemplos devem ser claros, corretos e análogos à tarefa desejada.
- **Custo de Tokens:** Few-shot prompts são mais longos e consomem mais tokens da janela de contexto do modelo, podendo ser uma limitação ou fator de custo.
- **Esforço de Criação:** Elaborar múltiplos exemplos de alta qualidade pode exigir mais tempo e esforço.
- **Ordem dos Exemplos (para Few-shot):** A ordem dos exemplos pode, às vezes, influenciar o resultado.

### 📝 Conclusão da Comparação

A escolha entre One-shot e Few-shot (N > 1) envolve equilibrar a necessidade de orientar o modelo com o custo e a complexidade de fornecer exemplos. Uma boa prática é começar pela abordagem mais simples (Zero-shot), avançar para One-shot se necessário e, caso a performance ainda precise melhorar, utilizar Few-shot (N > 1). A experimentação é essencial para determinar o número ideal de exemplos para cada tarefa e modelo.
