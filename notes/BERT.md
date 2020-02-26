# BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding

[paper url](https://arxiv.org/abs/1810.04805)

## Notes
BERT stands for Bidirectional Encoder Representations from Transformer. Unlike plain Transformer, BERT is conditioned on both left and right context in all layers. Due to this, BERT is able to achieve state-of-the-art results in various downstream NLU tasks (11 to be exact).

ELMO and GPT both uses unidirectional language model to learn language representation. The author argues that learning in unidirectional (left-to-right) model, where every token can attend to only previous token is a sub-optimal approach for sentence level tasks.


## Language pretraining
__Masked Language Model__: is used for For pretraining BERT as a pretraining objective. It is inspired by cloze task. While pre-training, random tokens from inputs are masked and the objective is to predict original tokens based on context. Contextual representation in BERT fuse both left and right context, which help in predicting the token.
__Next Sentence Prediction (NSP)__:
In addition to MLM, next sentence prediction task is jointy pre-trained using text pairs, for downstream tasks that uses text pairs as input. 

## Model Architecture

BERT is a multi-layer bi-directional Transformer encoder based on vanilla Transformer. The paper uses two model. BERT BASE has 12 transformer blocks, 768 Hidden size and 12 self-attention heads. BERT LARGE has 25 transformer blocks, 1024 Hidden size, 16 attention heads. BERT BASE has same size as OpenAI GPT  model.