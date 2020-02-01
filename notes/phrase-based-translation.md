# Phrase-Based & Neural Unsupervised Machine Translation

[paper url](https://arxiv.org/abs/1804.07755) 

## Notes


### Process:

#### Initialization:

Use Byte Pair Encoding (BPE) for tokenization and embedding
 1. Join both monolingual corpora
 1. Apply BPE tokenization on resulting corpus
 1. Learn Embeddings


#### Language Embedding:
Denoising autoencoding:
Denoising auto encoders are set of auto encoders that attempts to address identity function risk by randomly corrupting input that auto encoders must then reconstruct pr denoise. (For More: [visit link](https://skymind.ai/wiki/denoising-autoencoder) )


So for training a language model we use a noise model, which drops or swap some words from input and as demonising auto encoders learns about the original input.


### Algorithm :

 1. Learn Language models Ps and Pt over source and target language.
 1. Initial Translation models: Using Language models set (source and target) train two initial translation models, one in each direction, one from source to target and another from target to source.
 1. For k= 1 to N do:
  `Back Translation: Generate source and target sentences using current translation models P(k-1) t->s and P(k-1) s->t,
  factoring in language models Ps and Pt
  Train New Translation model P(k) s->t and P(k) t->s using generated sentences and leveraging Ps and Pt`


### Sharing Latent Representations:
Shared encoder representation act like an interlingua (encoding or decoding source and target language is possible using single encoder)
All the encoder and decoder parameters  (like embedding matrices) are shared across two language. Sharing decoder induces regularisation.


### Unsupervised PBSMT:
PBSMT = Phrase Based Statistical Machine Translation
Phrase base Machine Translation systems are known to perform well on low resource language pairs.

