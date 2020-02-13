# A CUTE - EVAL : Improved dialogue evaluation with optimized questions and multi-turn comparisons

[paper url](https://arxiv.org/abs/1909.03087)

## Notes

The paper points out that previously used human evaluation methods for dialogues doesn't help imrove the systems. Generally, automatic metric and human evaluations dont have any corelation. So paper attempts to introduce new evaaluation method, by introducing pairwise relative comparison setup for multi-turn dialoges.


Human judgements follow two general approaches, single turn pairwise evaluation and mutli-turn likert score. But these two approaches have limitations.
 - Single trun pairwise evaluations are only helpful for A/B testing. It is cheaper and faster as compared to second approach. But this approach will fail to test if model will repeat itself in multi-trun conversation setting.
 - Multi-turn Likert scores require the annotator to have multi-turn conversation and then provide integer score, which is more costly and time consuming. This approach suffer from bias and variance per annotator.

Method ACUTE-EVAL:

The method compares two dialogue model A and model B. This method asks human to compare side-by-side multi-turn dialogues conducted by these models.

1. Collect conversation logs for a model A and model B.
1. In a number of trials ask the annotators to make binary judgements between sampled pairwise conversations, and determine the winner either A or B.

These tests are performed in following settings:

1. Human-Model chats: In this setup, annotator is asked to evaluate two of previosuly obtained conversations, one between model A and human and other between model B and human.  And annotator is asked `Which speaker sounds more human?`.
1. Self Chats: In this setup, conversations between two models, model A and model B are recorded, and annotator is asked same question `which speaker sounds more human?`.

In both the settings annotator justifies their choice, which is also collected to decide which model wins.