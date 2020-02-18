# Deep Equilibrium Models

[paper url](https://arxiv.org/abs/1909.01377)

## Notes

Development of high capacity neural network is limited by shortage of memory devices. 
This paper tries to reduce the amount of memory necessary for a neural network by introducing a noval approach that finds optimal parameters directly by finding roots using quasi-Newton methods. 

The paper propose a Deep Equilibirium model (DEQ) that computes optimal parameters more quickly and backpropogates directly through the fixed point.

## The Deep Equilibrium Approach
The DEQ can be viewed as infinitely deep network, but the output is defined as the value which solves the some non-linear equation.

Benifits of weight tied network:
1. It act as form of regularization and stabilizes training and support generalization
1. It significantly reduce model size
1. Any deep network can be represented by a weight-tied DQN of equal depth by only increasing width
1. the network is improved due to feature abstractions as depth increases

What is the limit of this approach?
Each layer refines the previous one by combining temporal features across the sequence, increasing depth towards infinity berings diminishing returns.
In other words each additional layer has a smaller and smaller contribution untill the network reaches equilibirium.

### Forward pass:

The DEQ model output is the equilibrium point itself. The forward pass evaluation could be any procedure that solves for this equilibrium point.

### Backwards pass:

For backward pass we fix an algorithm (Newton's method is used in paper) and then store use gradient of the equilibrium model to calculate loss gradient. The backward gradient through infinite stacking can be represented by one step of matrix multiplication involving jacoiban equilibrium.