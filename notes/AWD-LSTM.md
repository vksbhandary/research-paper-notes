# Regularizing and Optimizing LSTM Language Models

[paper url](https://arxiv.org/abs/1708.02182)

## Notes

The paper focuses on optimizing LSTMs for word-level language modeling tasks.
Applying Optimization techniques on RNNs hasent proved useful due to various reasons. 
1. Dropout in RNN's hidden state is ineffective as it disrupts RNN's ability to retain long term dependency.
1. Normalization layer, batch normalization & recurrent normalization, introduce additional traning parameters and complicate training process and increase the sensitivity of model.
1. Regularizing RNN through limiting updates also hider the updates of randomly selected neuron.

The paper introduces weighted-dropped LSTM, averaged SGD (ASGD), 


## Averaged SGD (ASGD)
ASGD takes steps idential to SGD but instead of returning last iteration as solution it returns averaged weights of the past T iterations. If the averaging is triggered too soon the efficiency of the process is impacted.

## Weight-dropped LSTM

To prevent overfitting within recurrent connections of an RNN, DropConnect mask is used on recurrent hidden weight matrices. This process doesnt require any modification to an RNN formulation. The dropout is applied once to weight matrice before the forward and backward pass.

By performing  DropConnect to hidden-tohidden weight matrices within LSTM, we can prevent overfitting from occuring on recurrent connections of LSTM.

## Variable length backpropagation sequences

When the dataset is broken into fixed length batches dataset is not efficiently used. In order to prevent such inefficiency in data usage, the sequence length for forward and backward pass is randomly selected in two steps. First base sequence length is selected with probabilty p and seq/2 with probability 1-p. This spreads starting point for BPTT window beyond the base sequence length. Then sequence length is slected according to N(seq, s) where seq is base seqence length and s is standard deviation.