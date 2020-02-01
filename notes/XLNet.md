# XLNet: Generalized Autoregressive Pretraining for Language Understanding

[paper url](https://arxiv.org/abs/1906.08237) 

## Notes


Denoising Autoencoding based pertaining like BERT achieves better performance than pertaining approaches based on autoregressive language modeling.

Due to Masked inputs BERT suffers from pretrain-finetune discrepancy.

### What is XLNet?
XLNet is a generalised autoregressive pretraining method that :
 1. Enables learning bidirectional contexts by maximising the expected likelihood over all permutations of the factorization order
 1. Overcomes the limitations of BERT by using autoregressive formulation

XLNet incorporates idea from Transformer-XL, which is SOTA autoregressive model, into pretraining.


Most successful pretraining objectives are
 1. Autoregressive (AR) language modelling
 1. Autoencoding

AR language modelling pretraining method estimates the probability distribution of a text corpus using autoregressive model. AR language model is only trained to encode only uni-directional context, therefore it is not a effective modeling deep bidirectional contexts. Downstream NLP tasks require bi-directional context information.

Auto-encoding based pretraining does not perform explicit density estimation but it reconstructs the original data from corrupted input. Example is BERT.

