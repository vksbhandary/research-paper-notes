# Unified Language Model Pre-training for Natural Language Understanding and Generation

[paper url](https://arxiv.org/abs/1905.03197) 

## Notes

The paper indicates how the other language models just optimise on one or two types of unsupervised learning modelling objective.

But UNILM utilises all those modelling objectives left to right, right to left, bidirectional, and sequence to sequence.

The paper describes a set of cloze tasks, where a masked word is predicted based on its context.
These close tasks are different in how context is defined.
In case of left to right unidirectional LM, the context of the masked word to be predicted consists of all the words on its left.
For a right-to-left unidirectional LM, context consists of all the words on the right.
For a bidirectional LM, context consists of words on both left and right,
For a sequence to sequence LM, the context of the sequence is source sequence and words on the left of the target sequence.


Different masks are employed in order to control access to the context of the word to be predicted.

