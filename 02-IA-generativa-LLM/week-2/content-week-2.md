# Week 2

> Ajuste fino e avaliação de grandes modelos de linguagem

## Objetivos

- Descrever como o ajuste fino com instruções usando conjuntos de dados de solicitação pode melhorar o desempenho em uma ou mais tarefas

- Definir o esquecimento catastrófico e explicar as técnicas que podem ser usadas para superá-lo

- Definir o termo Parameter-efficient Fine Tuning (PEFT)

- Explicar como a PEFT diminui o custo computacional e supera o esquecimento catastrófico

- Explicar como o ajuste fino com instruções usando conjuntos de dados rápidos pode aumentar o desempenho do LLM em uma ou mais tarefas

## Conteúdo

### LLM fine-tuning process

![IA Generativa project lifeclicle](https://raw.githubusercontent.com/oliveiralex/assets-to-my-repos/main/02-IA-generativa-LLM/LLM-fine-tuning-process.png)
![IA Generativa project lifeclicle 2](https://raw.githubusercontent.com/oliveiralex/assets-to-my-repos/main/02-IA-generativa-LLM/LLM-fine-tuning-process-2.png)

### fine-tuning single task

![Fine tuning single task](https://raw.githubusercontent.com/oliveiralex/assets-to-my-repos/main/02-IA-generativa-LLM/LLM-fine-tuning-single-task.png)

### fine-tuning multi task

![Fine tuning multi task](https://raw.githubusercontent.com/oliveiralex/assets-to-my-repos/main/02-IA-generativa-LLM/LLM-fine-tuning-multi-task.png)


### LLM Evaluation - Metrics

- **Rouge**
    - Used for text summarization
    - Compare a summary to one or more reference summaries

- **BLEU score**
    - Used for text translation
    - Compares to human-generated translation 

### Parameter efficient fine-tuning (PEFT)

- Nesta técnica adiciona-se uma camada adicional com novos parâmetros;

- O Antigo modelo é ligeiramente modificado com esses "novos dados";

- Menos propenso ao *Catastrophic forgetting*;

- Alguns métodos do PEFT que podem ser utilizados são:

    - **Selective**: Seleciona um subconjunto inicial dos parâmetros do LLM para ajustar (fine-tune)

    - **Reparameterization**: Os pesos do modelo são reconfigurados (*reparameterization*) utilizando uma representação *low-rank*;

        - LoRA é uma das princiaps técnicas;

    - **Addtive**: Adiciona camadas ou parâmetros treináveis ao modelo;

## Questões aulas

### Questão 1: Catastrophic forgetting

#### Item 1

Quais das seguintes afirmações são verdadeiras em relação ao Esquecimento Catastrófico? Selecione todas as opções aplicáveis.

O esquecimento catastrófico ocorre quando um modelo de aprendizado de máquina esquece as informações aprendidas anteriormente à medida que aprende novas informações.
- [x] Correto
- [] Errado
**Justificativa**: A afirmação é verdadeira, e esse processo é especialmente problemático em cenários de aprendizado sequencial em que o modelo é treinado em várias tarefas ao longo do tempo.

#### Item 2

O esquecimento catastrófico só ocorre em tarefas de aprendizado supervisionado e não é um problema no aprendizado não supervisionado.
- [] Correto
- [x] Errado

**Justificativa**: O esquecimento catastrófico é um problema em tarefas de aprendizado supervisionado e não supervisionado. No aprendizado não supervisionado, ele pode ocorrer quando o modelo é treinado em um novo conjunto de dados diferente daquele usado durante o pré-treinamento.

#### Item 3

Uma maneira de atenuar o esquecimento catastrófico é usar técnicas de regularização para limitar a quantidade de alterações que podem ser feitas nos pesos do modelo durante o treinamento.
- [x] Correto
- [] Errado

**Justificativa**: Uma maneira de atenuar o esquecimento catastrófico é usar técnicas de regularização para limitar a quantidade de alterações que podem ser feitas nos pesos do modelo durante o treinamento. Isso pode ajudar a preservar as informações aprendidas durante as fases anteriores do treinamento e evitar o ajuste excessivo aos novos dados.

#### Item 4

O esquecimento catastrófico é um problema comum no aprendizado de máquina, especialmente em modelos de aprendizado profundo.
- [x] Correto
- [] Errado

**Justificativa**: Essa afirmação é verdadeira porque esses modelos normalmente têm muitos parâmetros, o que pode levar a um ajuste excessivo e dificultar a retenção de informações aprendidas anteriormente.


### Questão 2

Qual é a finalidade do ajuste fino com conjuntos de dados imediatos?


- [x] Para melhorar o desempenho e a adaptabilidade de um modelo de linguagem pré-treinado para tarefas específicas.
- [ ] Aumentar os recursos computacionais necessários para treinar um modelo de linguagem.
- [ ] Para eliminar a necessidade de instruções e avisos no treinamento de um modelo de linguagem.
- [ ] Diminuir a precisão de um modelo de linguagem pré-treinado com a introdução de novos prompts.

**Comentário:** Essa opção descreve com precisão a finalidade do ajuste fino com conjuntos de dados de prompts. Ela visa melhorar o desempenho e a adaptabilidade de um modelo de linguagem pré-treinado, treinando-o em tarefas específicas usando prompts de instrução.

### Questão 3

Os métodos de Parameter Efficient Fine-Tuning (PEFT) tentam abordar especificamente alguns dos desafios de realizar o treinamento fino completo.  Qual das opções a seguir descreve os desafios que o PEFT tenta superar?

- [x] Esquecimento catastrófico

    **Comentário**: Com o PEFT, a maioria dos parâmetros do LLM não é alterada, o que ajuda a torná-lo menos propenso a esquecimentos catastróficos.

- [ ] Desempenho do modelo

    **Comentário**: Embora os métodos PEFT ofereçam opções para treinar o modelo com mais eficiência, eles não tentam criar um modelo final que tenha melhor desempenho.

- [x] Restrições computacionais

    **Comentário**: Como a maioria dos parâmetros está congelada, normalmente só precisamos treinar de 15% a 20% dos pesos LLM originais, o que torna o processo de treinamento menos dispendioso (menos memória necessária)


- [x] Requisitos de armazenamento 

    **Comentário**: Com o PEFT, podemos alterar apenas uma pequena quantidade de parâmetros durante o ajuste fino, de modo que, durante a inferência, o senhor pode combinar o modelo original com os novos parâmetros, em vez de duplicar todo o modelo para cada nova tarefa que deseja realizar o ajuste fino.

## Tarefa: Questionário semana 2

**1.** Fill in the blanks: __________ involves using many prompt-completion examples as the labeled training dataset to continue training the model by updating its weights.  This is different from _________ where you provide prompt-completion examples during inference.
- [ ] In-context learning, Instruction fine-tuning 
- [ ] Prompt engineering, Pre-training
- [ ] Pre-training, Instruction fine-tuning
- [x] Instruction fine-tuning, In-context learning

**2.** Fine-tuning a model on a single task can improve model performance specifically on that task; however, it can also degrade the performance of other tasks as a side effect. This phenomenon is known as:
- [ ] Catastrophic loss
- [x] Catastrophic forgetting
- [ ] Instruction bias
- [ ] Model toxicity

**3.** Which evaluation metric below focuses on precision in matching generated output to the reference text and is used for text translation?
- [ ] HELM
- [x] BLEU
- [ ] ROUGE-2
- [ ] ROUGE-1

**4.** Which of the following statements about multi-task finetuning is correct? Select all that apply:
- [ ] Performing multi-task finetuning may lead to slower inference.
- [x] Multi-task finetuning can help prevent catastrophic forgetting.
- [x] FLAN-T5 was trained with multi-task finetuning.
- [ ] Multi-task finetuning requires separate models for each task being performed.

**5.** "Smaller LLMs can struggle with one-shot and few-shot inference:"

Is this true or false?
- [x] True
- [ ] False

**6.** Which of the following are Parameter Efficient Fine-Tuning (PEFT) methods? Select all that apply.
- [x] Reparametrization
- [ ] Subtractive
- [x] Selective
- [x] Additive

**7.** Which of the following best describes how LoRA works?
- [x] LoRA decomposes weights into two smaller rank matrices and trains those instead of the full model weights.
- [ ] LoRA freezes all weights in the original model layers and introduces new components which are trained on new data.
- [ ] LoRA trains  a smaller, distilled version of the pre-trained LLM to reduce model size
- [ ] LoRA continues the original pre-training objective on new data to update the weights of the original model.

**8.** What is a soft prompt in the context of LLMs (Large Language Models)?
- [x] A set of trainable tokens that are added to a prompt and whose values are updated during additional training to improve performance on specific tasks.
- [ ] A strict and explicit input text that serves as a starting point for the model's generation.
- [ ] A technique to limit the creativity of the model and enforce specific output patterns.
- [ ] A method to control the model's behavior by adjusting the learning rate during training.

**9.** "Prompt Tuning is a technique used to adjust all hyperparameters of a language model."

Is this true or false?
- [ ] True
- [x] False

**10.** "PEFT methods can reduce the memory needed for fine-tuning dramatically, sometimes to just 12-20% of the memory needed for full fine-tuning."

Is this true or false?
- [x] True
- [ ] False

## Recursos semana 2

- [Este artigo](https://arxiv.org/abs/2210.11416)
apresenta o FLAN (Fine-tuned LAnguage Net), um método de ajuste fino de instruções, e apresenta os resultados de sua aplicação. O estudo demonstra que, ao fazer o ajuste fino do modelo 540B PaLM em 1.836 tarefas e incorporar os dados do Chain-of-Thought Reasoning, o FLAN obtém melhorias na generalização, na usabilidade humana e no raciocínio de zero-shot em relação ao modelo básico. O documento também fornece informações detalhadas sobre como cada um desses aspectos foi avaliado.

- [Recursos week 2](https://www.coursera.org/learn/generative-ai-with-llms/supplement/zlpBf/week-2-resources)
