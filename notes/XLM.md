# Cross-lingual Language Model Pretraining

[paper url](https://arxiv.org/abs/1901.07291) 

## Notes


Generative retraining method is efficient for NLU of English.
Proposes two methods to learn cross-lingual language model
1. Unsupervised that relies on monolingual data
1. Supervised that leverages parallel data


### cross-lingual language model objective:

 1. Shared sub-word vocabulary: all languages are processed with the same shared vocabulary created through Byte Pair Encoding (BPE). BPE splits on the concatenation of sentences is leant. The sentences are randomly sampled from monolingual corpora.
 1. Casual Language modeling (CLM): In this modeling task we train a transformer to predict the probability of a word given previous words in sentences.
 1. Masked Language modeling (MLM): This modeling task uses objective of task called “Cloze task”. Where we train a language model where 15% of BPE tokens are replaced by MASK 80% of the time, other 10% of the time it is replaced by random token and for rest of 10% of the time they are kept unchanged. The main difference from other method is that here input tokens are fixed to 256 tokens.
 1. Translation Language Modeling (TLM): In this language modelling task we concatenate parallel sentences and words are masked randomly in both and target sentences.
 1. Cross-lingual Language model pretraining (XLM): This method makes use of either one or both model pretraining CLM, MLM. This model is trained with batches of 64 streams of continuous sentences composed of 256 tokens.