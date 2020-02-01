# Unsupervised Machine Translation Using Monolingual Corpora Only

[paper url](https://arxiv.org/abs/1711.00043) 


## Notes

### Abstract

1. Propose a model that takes sentences from monolingual corpora in two different language and maps them into same latent space.
1. By learning to reconstruct in both languages from this shared feature space, model effectively learns to translate without using any labeled data.

### Overview of method:

The translational mode starts with an unsupervised naive translational model obtained by making word-by-word translation of sentences using a parallel dictionary

At each iteration,
 1. encoder and decoder are trained by minimising an objective function that measures their ability to reconstruct and translate from a noisy version of an input training sentences.
 1. Noisy version is obtained by dropping and swapping words in case of auto-encoding tasks.
 1. A discriminator model is trained in an adversarial settings to promote alignment of latent distribution of sentences in the source and target domains.
 1. Newly learned encoder/decoder are then used at the next iteration to generate new translations until convergence of the algorithm

