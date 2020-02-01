# Attention Is All You Need

[paper url](https://arxiv.org/abs/1706.03762)

## Notes


### What is wrong with RNNs?
Recurrent neural networks (RNN) are being used as established state-of-the-art for quite a while now (at the time of publication of this paper). Due to its inherent definition of RNN architecture, there are a few problems with RNN.

1. While training a recurrent network, we need to compute hidden state for each input tokens. Which makes it very painful to train on GPU. As we can not parallelize the process. 
1. learning long range dependency in recurrent networks is still a problem, although improvements in recurrent architecture like LSTMs & GRU have greatly reduced the problem. Still it is very hard for RNN to learn long range dependencies.


This paper introduces a new Transformer architecture of neural network to:
1. parallelize the process and improve it as compared to sequence models (RNN, LSTM, GRU)
1. allow modeling of dependencies without regard to their distance in the input or output sequences
1. Reduce the number of sequential computations (in Transformer it is o(1)) to learn dependency between two words in input and output sequence.
1. Attempt to improve the language translation (that a bonus point)


The proposed architecture completely eschew recurrence and convolutions, and depends only on self attention mechanism for building the relationship between input and output sequence. 

### Attention mechanism

Basic intuition of the attention process is that, it focuses on only some part of input by filtering out the rest of input sequence.  Mathematically, the process uses key, value, input pair to compute output of mechanism called __self-attention__.





