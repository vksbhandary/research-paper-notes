# The Evolved Transformer

[paper url](https://arxiv.org/abs/1901.11117)

## Notes


### Introduction

Neural architecture search (NAS) has begun to outperform human-designed models. The paper tries to utilize the NAS to create better architecture. The architecture proposed in this paper shows consistent improvement over transformer on four well-established language translation tasks.


With NAS better feed-forward achitectures for seq2seq tasks can be designed. Tournament selection architeture search and warm start are applied with transformer, to search for better transformer architecture.


### Torunament selection process:

1. Define a gene encoding that describes a neural network architecture
1. Create initial population by randomly sampling from space of gene encoding.
1. The individuals are trained and assigned fitness (in this case its negative log perplexities on WMT 14En-De validation set)
1. Then the population is sampled to produce subpopulations, where highest fitness candidates are selected as parent.
1.  Selected parent's gene encoding is mutated to produce child models
1. Then child models are assigned fitness via training and evaluating on target task just like initial population.
1. After fitness evaluation, the population is sampled once again, individual in subpopulation with lowest fitness is removed from population.
1. Newly evaluated child models are added to population, taking place of removed population.
1. This process is repseated, and inventually it results in a population with high fitness individuals.


