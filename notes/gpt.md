# Improving Language Understanding by Generative Pre-Training

[paper url](https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/language-unsupervised/language_understanding_paper.pdf) 


## Notes

The paper demonstartes that the performance of language models in NLU tasks can be improved using generative pre-training on unlabeled corpus. Inputs in the proposed method are transformed to reflect on the task.

The training consists of two stages:
1. Learning high capacity language model
1. Fine-tuning the model for tasks such as NER, Classification, translation,  etc.

Pretraining:

Unsupervised pretraining objective maximize the loglikelyhood of next word given k window size using stochastic gradiant decent algorithm. They use variant of multi-layer transformer encoder and use similar approach used in paper "Attention is all you need"


Finetuning:
After unsupervised training, the model is trained using different dataset in a supervised setting. Inputs are passed through pretrained model and final output of the transformer encoder block's activation is used to feed into linear layers.


Input transoformations:

Input is transformed into different form based on final task of the model. In case of similarity input is ordered into a set of two sentences. For question answering the context and questions is set as input with delimiter token in between.