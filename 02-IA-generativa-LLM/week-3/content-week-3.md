# Week 3
> Aprendizado por reforço e aplicativos com LLM

## Objetivos

- Descrever como o RLHF usa o feedback humano para melhorar o desempenho e o alinhamento de grandes modelos de linguagem
    
- Explique como os dados coletados de rotuladores humanos são usados para treinar um modelo de recompensa para RLHF
    
- Definir o estímulo de cadeia de pensamento e descrever como ele pode ser usado para melhorar as habilidades de raciocínio e planejamento dos LLMs
    
- Discuta os desafios que os LLMs enfrentam com os limites de conhecimento e explique como as técnicas de recuperação e aumento de informações podem superar esses desafios

## Conteúdo

- Modelos podem se comportar de uma forma ruim:
    - Linguagem tóxica
    - Respostas agressivas
    - Fornecer informações perigosas

- Isso está muito ligado a origem dos dados (oriundos da internet);

- Princípio HHH - Helpful, Honest and Harmless, são um conjunto de princípios que orientam orientam os desenvolvedores de IA;

- Reinforcement learning from human feedback (RLHF)
    - Maximize helpfulness
    - Minimize harm
    - Avoid dangerous topics

- **Reinforcement Learning (RL)**

    - Paradigma de aprendizado de máquina no qual um agente interage com um ambiente dinâmico e aprende a realizar ações para maximizar uma recompensa;

    - No RL, o agente toma decisões sequenciais em um ambiente incerto, recebendo feedback na forma de recompensas ou penalidades após cada ação;

    - O objetivo é aprender uma política ou estratégia que maximize a recompensa ao longo do temp;
    
    - O agente explora diferentes ações para descobrir quais levam a resultados mais vantajosos, ao mesmo tempo em que aproveita as informações aprendidas para aprimorar suas decisões futuras.

- Os modelos LLM podem ser integrados com nossas aplicações, mas para isso, precisamos pensar em algumas variáveis;

- Técnicas para otimização do modelo para melhorar a performance da aplicação, cujo objetivo é reduzir tamanho do LLM.

- Temos 3 técnicas para otimização:

    - **Distillation**: 
    
        - Concentra em fazer com que um modelo maior (*teacher*) treine um modelo menor (*student*). A ideia é que o student "aprende" a imitar estatisticamente o comportamento do *teacher*.

        - Train a smaller student model from a larger teacher model;

    - **Quantization**:

        - Reduce precision of model weights

    - **Prunning**:

        - Reduce model weights with values close or equal to zero.

- Tempo e esforço no ciclo de vida

![steps-lifecicle-LLM](https://raw.githubusercontent.com/oliveiralex/assets-to-my-repos/main/02-IA-generativa-LLM/time-effort-lifecycle.png)

- Retrieval augmented generation (RAG)

    - Utilização de fontes de dados externas para superar algumas limitações dos modelos, como dados desatualizados;

    - Permite atualizar regularmente o modelo com novos conhecimentos.

    - Neste caso, não é necessário retreinar o modelo (efford/$$$ expensive)

- O LLM pode apresentar algumas limitações em algumas operações matemáticas e tarefas de raciocínio lógico, podendo levar a erros de cálculos ou respostas imprecisas.

- Uma ideia para torna-los mais precisos  é integrá-los com um interpretador Python por exemplo, o que é chamado de **Program-aided language (PAL) models**.


## Questões aulas:

### Questão 1:

Ao usar o aprendizado por reforço com feedback humano (RLHF) para alinhar grandes modelos de linguagem com as preferências humanas, qual é a função dos rotuladores humanos?

- [ ] Para identificar os pesos do modelo que devem ser atualizados
- [x] Para pontuar as conclusões imediatas, de modo que essa pontuação seja usada para treinar o componente do modelo de recompensa do processo RLHF.
- [ ] Comparar as conclusões originais do LLM com as conclusões do modelo atualizado do RLHF e garantir que não haja muita divergência.
- [ ]Escrever prompts e conclusões do zero que são usados durante o ajuste fino com o RLHF

**Comentário**: No RLHF, os rotuladores humanos pontuam um conjunto de dados de conclusões do modelo original com base em critérios de alinhamento como utilidade, inocuidade e honestidade. Esse conjunto de dados é usado para treinar o modelo de recompensa que pontua as conclusões do modelo durante o processo de RLHF.

### Questão 2


## Tarefa: Questionário semana 3

**1.** Which of the following are true in regards to Constitutional AI? Select all that apply.
- [x] Red Teaming is the process of eliciting undesirable responses by interacting with a model.
- [ ] For constitutional AI, it is necessary to provide human feedback to guide the revisions.
- [x] To obtain revised answers for possible harmful prompts, we need to go through a Critique and Revision process.
- [x] In Constitutional AI, we train a model to choose between different prompts.

**2.** What does the "Proximal" in Proximal Policy Optimization refer to?
- [ ] The algorithm's ability to handle proximal policies
- [ ] The algorithm's proximity to the optimal policy
- [ ] The use of a proximal gradient descent algorithm
- [x] The constraint that limits the distance between the new and old policy

**3.** "You can use an algorithm other than Proximal Policy Optimization to update the model weights during RLHF."

Is this true or false?
- [x] True
- [ ] False

**4.** In reinforcement learning, particularly with the Proximal Policy Optimization (PPO) algorithm, what is the role of KL-Divergence? Select all that apply.
- [x] KL divergence measures the difference between two probability distributions.
- [x] KL divergence is used to enforce a constraint that limits the extent of LLM weight updates.
- [ ] KL divergence encourages large updates to the LLM weights to increase differences from the original model.
- [ ] KL divergence is used to train the reward model by scoring the difference of the new completions from the original human-labeled ones.

**5.** Fill in the blanks: When fine-tuning a large language model with human feedback, the action that the agent (in this case the LLM) carries out is ________ and the action space is the _________.
- [x] Generating the next token, vocabulary of all tokens.
- [ ] Processing the prompt, context window.
- [ ] Calculating the probability distribution, the LLM model weights.
- [ ] Generating the next token, the context window

**6.** How does Retrieval Augmented Generation (RAG) enhance generation-based models?
- [ ] By applying reinforcement learning techniques to augment completions. 
- [x] By making external knowledge available to the model
- [ ] By increasing the training data size.
- [ ] By optimizing model architecture to generate factual completions.

**7.** How can incorporating information retrieval techniques improve your LLM application? Select all that apply.
- [x] Overcome Knowledge Cut-offs
- [ ] Faster training speed when compared to traditional models
- [ ] Reduced memory footprint for the model
- [x] Improve relevance and accuracy of responses

**8.** What is a correct definition of Program-aided Language (PAL) models?
- [x] Models that offload computational tasks to other programs.
- [ ] Models that integrate language translation and coding functionalities.
- [ ] Models that assist programmers in writing code through natural language interfaces.
- [ ] Models that enable automatic translation of programming languages to human languages.

**9.** Which of the following best describes the primary focus of ReAct?
- [ ] Investigating reasoning abilities in LLMs through chain-of-thought prompting.
- [ ] Studying the separate topics of reasoning and acting in LLMs.
- [ ] Exploring action plan generation in LLMs.
- [x] Enhancing language understanding and decision making in LLMs.

**10.** What is the main purpose of the LangChain framework?
- [x] To chain together different components and create advanced use cases around LLMs, such as chatbots, Generative Question-Answering (GQA), and summarization.
- [ ] To evaluate the LLM's completions and provide fast prototyping and deployment capabilities.
- [ ] To connect with external APIs and datasets and offload computational tasks.
- [ ] To provide prompt templates, agents, and memory components for working with LLMs.


## Recursos semana 3

- Aprendizado por reforço com feedback humano (RLHF)

    - [Treinamento de modelos de linguagem para seguir instruções com feedback humano](https://arxiv.org/pdf/2203.02155.pdf) - Documento da OpenAI introduzindo um processo humano no circuito para criar um modelo que seja melhor em seguir instruções (InstructGPT).

- [Recursos week 3](https://www.coursera.org/learn/generative-ai-with-llms/supplement/89tR9/week-3-resources)

