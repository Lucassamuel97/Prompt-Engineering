[⬅️ Voltar para o README](./README.md)

# Directional Stimulus / Directed Prompting

**Directed Prompting** (ou *Directional Stimulus Prompting*) é uma técnica que guia a resposta do modelo ao utilizar verbetes, comandos ou estímulos direcionais. Diferente de prompts abertos ou vagos, essa abordagem indica como o modelo deve pensar ou responder, influenciando estilo, formato, foco ou tipo de raciocínio esperado.

## Quando utilizar

- Obter respostas previsíveis ou formatadas.
- Guiar o raciocínio para um estilo de resposta desejado.
- Exigir respostas em formato parseável (JSON, XML, YAML).
- Focar a resposta em um papel ou contexto específico (ex: "responda como um arquiteto", "explique em tópicos").

## Benefícios

- Reduz ambiguidade e alucinação.
- Padroniza a forma da resposta.
- Melhora a utilidade programática da saída (ex: para scripts ou interfaces).
- Permite controle do comportamento do modelo sem complexidade adicional.

## Link do Paper

- [Prompting for Control: A Study of Directional Stimulus](https://arxiv.org/abs/2203.11171)

## Exemplos de comandos direcionais

- `Liste...`
- `Compare...`
- `Explique com exemplos...`
- `Responda em formato JSON`
- `Justifique cada item`
- `Explique como um arquiteto sênior faria`
- `Divida em tópicos: contexto, estratégia, riscos e conclusão`

Esses comandos atuam como estímulos condicionais, alterando formato e profundidade da resposta.

## Aplicações em engenharia de software

- Gerar documentação técnica estruturada.
- Listar vantagens/desvantagens de soluções de arquitetura.
- Descrever fluxos de autenticação, cache, filas, escalabilidade.
- Padronizar output para consumo por sistemas (JSON, YAML).

### Exemplo de Directed Prompting

**Prompt:**  
Compare as tecnologias Kafka, RabbitMQ e Amazon SQS para uso em sistemas distribuídos. Responda nos tópicos: características principais, throughput, confiabilidade, complexidade operacional e quando usar cada uma.

**Resposta esperada:**

#### Kafka
- **Características:** distribuído, baseado em logs, alta durabilidade.
- **Throughput:** muito alto, ideal para big data e pipelines de evento.
- **Confiabilidade:** altíssima, com replicação e retenção configurável.
- **Complexidade:** alta — exige setup de brokers, Zookeeper (ou KRaft), monitoração ativa.
- **Quando usar:** quando o volume de dados é alto e a ordem das mensagens é crítica.

#### RabbitMQ
- **Características:** orientado a fila, com suporte a múltiplos protocolos (AMQP, MQTT).
- **Throughput:** médio-alto, mais rápido para mensagens pequenas.
- **Confiabilidade:** boa, com suporte a ACK, DLQ e persistência.
- **Complexidade:** moderada, bom tooling e fácil operação.
- **Quando usar:** para mensageria tradicional, RPC e integração entre serviços.

#### Amazon SQS
- **Características:** gerenciado, escalável automaticamente, simples de operar.
- **Throughput:** escalável sob demanda.
- **Confiabilidade:** excelente, com redundância e reentrega automática.
- **Complexidade:** baixa — sem servidores para administrar.
- **Quando usar:** quando se busca simplicidade e escalabilidade sem overhead de operação.


## Comparação com Skeleton of Thought (SoT)
**Skeleton of Thought (SoT)** e **Directed Prompting** são técnicas de prompting que possuem propósitos e estruturas diferentes. Abaixo está uma tabela comparativa para destacar as principais diferenças:

| Aspecto | Skeleton of Thought | Directed Prompting |
| :--- | :--- | :--- |
| **Tipo de controle** | Estrutura rígida com seções definidas | Estímulo leve baseado em instruções textuais |
| **Modelo deve seguir tópicos?** | Sim | Não necessariamente |
| **Liberdade de formatação** | Baixa | Média |
| **Uso típico** | Documentações, especificações, planejamento | Comparações, respostas formatadas, controle de estilo |
| **Exemplo de prompt** | "Preencha os tópicos: visão geral, arquitetura, riscos, conclusão."| "Liste as vantagens e desvantagens da arquitetura em tópicos." |