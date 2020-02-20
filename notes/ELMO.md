# Deep contextualized word representations

[paper url](https://arxiv.org/abs/1802.05365)

## Notes

Learning high quality pre-trained representations of words can be challenging as it should capture both characteristics of word use and how the usage vary across other contexts.

The paper introduces new type of deep contextualized word representation that directly address these challenges.

This representation differ from traditional embeddings such that each token's embedding depends on entire input sentence. The embeddings are derived from bidrectional LSTM which is trained with a coupled language model objective on a large text corpus.

ELMO representations are unique in the sense that they are dependent on all internal layers of biLM. This makes word representatiosn very rich. LSTM states captures context-dependent aspects of word meaning and aspacts of syntax.

### Training
A forward langage model computes propability of sequence by modelling probability of next token. The model is trained such that at each position, each layer outputs context dependent representation. The top LSTM output is used to predict next token with a softmax layer.

Similarly a backward LM is simimlar to forward LM except it runs over the sequence in reverse predecting the previous token.

A biLM combines both forward and backward LM such that log likelihood of both forward and backwards directions are maximized. ELMO model shares some wrights between directions instead of using completely independent parameters.

