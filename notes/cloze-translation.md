# Unsupervised Question Answering by Cloze Translation

[paper url](https://arxiv.org/abs/1906.04980)

## Notes

### Introduction

Due to recent advances human performance is within reach QA dataset. But 

The paper attempts to explore if quality extractive QA data can be generated using only the unlabelled data in an un-supervised setting. The approach used by the paper uses context, question and answer triplet to train a model.

### Proposed method to generate QA dataset:

1. Sample a paragraph in target domain
1. Sample candidate answers within the context, usingpretrained NER
1. Extract fill-in-the-blank cloze question
1. Convert cloze question into natural questions using unsupervised close-to-normal question translator.

Conversion of cloze question into natural question is the most challenging step. So it is tackled by using seq2seq model to map between natural and cloze question using online back-translation and denoising auto-encoding.

