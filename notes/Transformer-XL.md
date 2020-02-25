# Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context

[paper url](https://arxiv.org/abs/1901.02860) 

## Notes

The paper explores the idea of learning dependency beyond a fixed length without disrupting temporal coherence, as language models are limited by fixed length context in language modeling.

It proposes two noval method to resolve context fragmentation problem and reduce the evaluation time as compared to transformer.


## Context fragmentation problem

As the consequence of fixed length attention, the model can not capture longer-term dependency beyond the predefined context length. Therefore, model lacks necessary contextual information needed to predict the first few symbols leadnig to inefficient optimization and infirior performance. This problem is reffered to as context fragmentation

## 1. Recurrence in self attention

The paper introduces notion of recurrence in deep self-attention network.  Instead of computing hidden state from scratch for each new segment, the proposed method reuse the hidden state obtained from previous segments.

Previous hidden state serve as a memory of current segment which builds up reccurrent connection between the segments. This results in building long-term dependency as information si propagated through the recurrent conncetion.

## 2. Relative positional encoding
Positional information is provided as input in a transformer architecture. The actual input to transformer is element-wise addition of word embeddings and the positional encodings. 

Instead of using positional encoding as bias into initial embedding, it is injected into the attention socre of each layer. The paper adapts this positional encoding to the recurrent mechanism by injecting the relative distance dynamically into the attention score of each layer. This makes state reuse mechanism feasable and there isnt any loss of temporal information as the position can be recovered recursively from relative distance.

