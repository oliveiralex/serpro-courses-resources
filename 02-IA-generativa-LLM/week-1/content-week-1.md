# Week 1

> Casos de uso de IA generativa, ciclo de vida do projeto e pré-treinamento do modelo

## Objetivos

- Discuta o pré-treinamento do modelo e o valor do pré-treinamento contínuo versus o ajuste fino

- Definir os termos IA geradora, modelos de linguagem grandes, prompt e descrever a arquitetura do transformador que alimenta os LLMs

- Descreva as etapas de um ciclo de vida típico de um modelo de IA generativo e baseado em LLM e discuta os fatores restritivos que orientam as decisões em cada etapa do ciclo de vida do modelo

- Discutir os desafios computacionais durante o pré-treinamento do modelo e determinar como reduzir com eficiência o espaço ocupado pela memória

- Defina o termo lei de escalonamento e descreva as leis que foram descobertas para LLMs relacionadas ao tamanho do conjunto de dados de treinamento, orçamento de computação, requisitos de inferência e outros fatores.

## Conteúdo

### IA Generativa project lifeclicle

![Texto Alternativo](https://raw.githubusercontent.com/oliveiralex/assets-to-my-repos/main/02-IA-generativa-LLM/GenAI-life-cicle.png)

## Questões aulas

### Questão 1: Métodos treinamento LLM

Qual método de aprendizagem dentro do contexto envolve a criação de um prompt inicial que indica a tarefa a ser concluída e inclui um único exemplo de pergunta com resposta, seguido de uma segunda pergunta a ser respondida pelo LLM? 

**Resposta:** A inferência de uma chance envolve o fornecimento de um exemplo de pergunta com resposta, seguido de uma segunda pergunta a ser respondida pelo LLM. A inferência de poucas tentativas fornece vários exemplos de prompts e respostas, enquanto a inferência de zero tentativas fornece apenas um prompt a ser respondido pelo LLM.

### Questão 2: Configuração parâmetros

Qual parâmetro de configuração para inferência pode ser ajustado para aumentar ou diminuir a aleatoriedade na camada de saída do modelo?  

**Resposta:** A temperatura é usada para afetar a aleatoriedade da saída da camada softmax. Uma temperatura mais baixa resulta em variabilidade reduzida, enquanto uma temperatura mais alta resulta em maior aleatoriedade da saída.

### Questão 3: Paralelismo de Dados

O paralelismo de dados é uma estratégia que divide os dados de treinamento em várias GPUs. Cada GPU processa um subconjunto diferente dos dados simultaneamente, o que pode acelerar bastante o tempo total de treinamento.

### Questão 4: Avalie as afirmações e justifique

#### Item 1

Para dimensionar nosso modelo, precisamos aumentar conjuntamente o tamanho do conjunto de dados e o tamanho do modelo, ou eles podem se tornar um gargalo um para o outro.
- [x] Verdadeiro
- [] Falso

**Justificativa:** Por exemplo, embora o aumento do tamanho do conjunto de dados seja útil, se não melhorarmos conjuntamente o tamanho do modelo, ele poderá não ser capaz de capturar o valor do conjunto de dados maior.

#### Item 2

Há uma relação entre o tamanho do modelo (em número de parâmetros) e o número ideal de tokens para treinar o modelo.
- [x] Verdadeiro
- [] Falso 

**Justificativa:** Essa relação é descrita no artigo de Chinchilla, que mostra que muitos modelos podem até ser superparametrizados de acordo com a relação encontrada.

#### Item 3
Ao medir o orçamento de computação, podemos usar "PetaFlops por segundo-dia" como uma métrica.  
- [x] Verdadeiro
- [] Falso 

**Justificativa:** Petaflops por segundo-dia é uma medida útil para o orçamento de computação, pois reflete o hardware e o tempo necessários para treinar o modelo.

#### Item 4

O senhor deve sempre seguir o número recomendado de tokens, com base nas leis da chinchila, para treinar seu modelo
- [] Verdadeiro
- [x] Falso 

**Justificativa:** Embora a otimização da computação seja importante, pode ser um desafio obter uma quantidade suficiente de tokens de dados. No caso do BloombergGPT, eles tinham uma contagem limitada de tokens e até usaram menos tokens devido à interrupção antecipada. Embora as leis da chinchila ofereçam orientações valiosas, elas não devem ser seguidas estritamente como regras rígidas.


## Tarefa: Questionário 1 (<sub><sup>[link pt-br](quiz-pt-br.md)</sup></sub>)

**1.** Interacting with Large Language Models (LLMs) differs from traditional machine learning models. Working with LLMs involves natural language input, known as a _____, resulting in output from the Large Language Model, known as the ______.

Choose the answer that correctly fill in the blanks.
- [ ] tunable request, completion
- [x] prompt, completion
- [ ] prediction request, prediction response
- [ ] prompt, fine-tuned LLM

**2.** Large Language Models (LLMs) are capable of performing multiple tasks supporting a variety of use cases. Which of the following tasks supports the use case of converting code comments into executable code?
- [x] Translation
- [ ] Information Retrieval
- [ ] Text summarization
- [ ] Invoke actions from text

**3.** What is the self-attention that powers the transformer architecture?
- [ ] The ability of the transformer to analyze its own performance and make adjustments accordingly.
- [x] A mechanism that allows a model to focus on different parts of the input sequence during computation.
- [ ] A measure of how well a model can understand and generate human-like language.
- [ ] A technique used to improve the generalization capabilities of a model by training it on diverse datasets.

**4.** Which of the following stages are part of the generative AI model lifecycle mentioned in the course? (Select all that apply)
- [x] Deploying the model into the infrastructure and integrating it with the application.
- [x] Defining the problem and identifying relevant datasets.
- [ ] Performing regularization
- [x] Manipulating the model to align with specific project needs.
- [x] Selecting a candidate model and potentially pre-training a custom model.

**5.** "RNNs are better than Transformers for generative AI Tasks."

Is this true or false?
- [ ] True
- [x] False

**6.** Which transformer-based model architecture has the objective of guessing a masked token based on the previous sequence of tokens by building bidirectional representations of the input sequence.
- [x] Autoencoder
- [ ] Autoregressive
- [ ] Sequence-to-sequence

**7.** Which transformer-based model architecture is well-suited to the task of text translation?
- [ ] Autoencoder
- [ ] Autoregressive
- [x] Sequence-to-sequence

**8.** Do we always need to increase the model size to improve its performance?
- [ ] True
- [x] False

**9.** Scaling laws for pre-training large language models consider several aspects to maximize performance of a model within a set of constraints and available scaling choices. Select all alternatives that should be considered for scaling when performing model pre-training?
- [ ]Batch size: Number of samples per iteration 
- [x] Model size: Number of parameters
- [x] Dataset size: Number of tokens
- [x] Compute budget: Compute constraints

**10.** "You can combine data parallelism with model parallelism to train LLMs."

Is this true or false?
- [x] True
- [ ] False


## Recursos Semana 1

### Ciclo de vida da IA generativa

- [IA generativa no AWS: Building Context-Aware, Multimodal Reasoning Applications (Criando aplicativos de raciocínio multimodal com reconhecimento de contexto](https://www.amazon.com/Generative-AI-AWS-Multimodal-Applications/dp/1098159225/)

### Arquitetura do Transformer

- [Attention is All You Need](https://arxiv.org/pdf/1706.03762.pdf) - Este artigo apresentou a arquitetura Transformer, com o mecanismo central de "auto-atenção". Esse artigo foi a base para os LLMs.

- [BLOOM: BigScience 176B Model ](https://arxiv.org/abs/2211.05100) - O BLOOM é um LLM de código aberto com 176B parâmetros treinados de forma aberta e transparente. Neste artigo, os autores apresentam uma discussão detalhada do conjunto de dados e do processo usado para treinar o modelo. O senhor também pode ver uma visão geral de alto nível do modelo

- [Modelos de espaço](https://www.coursera.org/learn/classification-vector-spaces-in-nlp) vetorial - Série de lições da especialização em processamento de linguagem natural do DeepLearning.AI que discute os conceitos básicos dos modelos de espaço vetorial e seu uso na modelagem de linguagem.

### Outros recursos

- [Recursos week 1](https://www.coursera.org/learn/generative-ai-with-llms/supplement/kRX5c/week-1-resources)