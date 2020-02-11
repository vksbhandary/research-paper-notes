# Towards a Human-like Open-Domain Chatbot

[paper url](https://arxiv.org/abs/2001.09977)

## Notes

Chatbots often respond to open ended questions with a vague, generic or a nonsensical response. The paper represents Meena which is trained on 40B words minded from social media conversations.

With Meena, authors try to experiment with end-to-end chatbot approach. The paper attempts to find corelation betweeen human evaluation metric called sensibleness and specificity average (SSA) and perplexity of next token in an end-to-end neural network based chatbot.


### Model used
The best performing modal in this study is derived from Evolved Transformer, which is a seq2seq modal with 2.6B parameters (it includes 1 ET encoder and 13 ET decode block) based on Transformer architecture. The modal is trained on input sequence with all turns of context (upto 7) and preffered response is set to output sequence.


### Evluation

The model is evaluated in two different settings. In static settings a curated dataset with 1477 multi-turn conversation is used. In interactive setting, humans are allowed to chat about anything they want.

SSA metric shows strong correlation with Meena's perplexity in both settings. Which means training Meena more makes the model's responses more specific and sensible.