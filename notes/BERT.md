# BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding

[paper url](https://arxiv.org/abs/1810.04805)

## Notes
BERT stands for Bidirectional Encoder Representations from Transformer. Unlike plain Transformer, BERT is conditioned on both left and right context in all layers. Due to this, BERT is able to achieve state-of-the-art results in various downstream NLU tasks (11 to be exact).

ELMO and GPT both uses unidirectional language model to learn language representation. The author argues that learning in unidirectional (left-to-right) model, where every token can attend to only previous token is a sub-optimal approach for sentence level tasks.


## Language pretraining

__Masked Language Model__: is used for For pretraining BERT as a pretraining objective. It is inspired by cloze task. Bi-directional conditioning allows the input to indirectly see itself and model could predict target word in a multi-layered context. Inorder to prevent this, some random tokens from input sequence are masked while pre-training and the objective is to predict original tokens based on context. Contextual representation in BERT fuse both left and right context, which help in predicting the masked token.

1. The final hidden vectors corresponding to the mask tokens are fed into an output softmax over the vocabulary (as in a standard LM).
1. This task create mismatch between pre-training and finetuning as __[MASK]__ token doesnt appear in downward task's input (its downside of this approach)
1. To mitigate above downside, for each 15% of selected tokens:
	- 80% of the times selected token is replaced with __[MASK]__ 
	- 10% of times selected token is replaced with random token
	- 10% of times selected token is left unchanged


__Next Sentence Prediction (NSP)__:
In addition to MLM, next sentence prediction task is used to pre-train the model using text pairs. As many downstream NLP tasks are based on relationships between two sentences. Monolingual corpus can be used to pre-train model for binarized *binarized next sentence prediction* task.
1. 50% of times when choosing sentences A and B, B is actual next sentence that follows A (labeled as __InNext__).
1. 50% of time A and B are random sentences from corpus(labeled as __NoNext__).


## Model Architecture

BERT is a multi-layer bi-directional Transformer encoder based on vanilla Transformer. The paper uses two model. BERT BASE has 12 transformer blocks, 768 Hidden size and 12 self-attention heads. BERT LARGE has 25 transformer blocks, 1024 Hidden size, 16 attention heads. BERT BASE has same size as OpenAI GPT  model.


## Input/Output Representations

In order to make BERT able to handle tasks which require pair of sentences and a single sentence, it is trained in both settings.

1. To represent two pair of sentences in a single sequence token __[SEP]__ is used to seprate them.
1. For a given token its input representations is constructed by adding corresponding token, segment, position embedding
1. First token of every sequence repreents special class token __[CLS]__.
1.  Final hidden state of __[CLS]__ token is used as aggregate sequence representation for classification.
1. Paper uses Wordpiece embedding with only 30k token vocabulary.

## Pretraining data
For BERT pre-training BooksCorpus (800M words) and English Wikipedia (2500M words) are used. For wikipedia only text passages are used tables, list headers are ignored.

## Fine-Tuning BERT
Compared to Pre-training, Fine-tuning is inexpensive as all the state-of-the-art results can be achieved with a few Hours of GPU training or 1 Hour of single TPU training.
For different downstream task model is trained differently with available pairs of inputs and output.

## Effect of Pre-training Tasks

Terms used below
- __No NSP__: A bidirectional model is trained onlu using MLM objective.
- __LTR & No NSP__: A left context only model is trained using standard Left-to-right (LTR) language model. 
- __BiLSTM__: A type of recurrent network with two LSTM layers.

1. Removing NSP hurts perfromance of QNLI, MNLI, SQuAD 1.1
1. LTR & No NSP performs worse as compared to No NSP on all tasks.
1. Adding BiLSTM on top of LTR significantly improved results on SQUAD, but worse than original BERT model
1. BiLSTM's performance is worse on GLUE tasks.
