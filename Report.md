## Introduction

This project is a DDPG (Deep deterministic policy gradient) implementation to solve an environment consisting
in a mechanical arm trying to reach the given position as long as possible. The implementation is based on the bipedal
implementation provided by Udacity [here](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-bipedal).

## Network architecture

The DDPG algorithm uses two networks, and actor and a critic. The architecture of these networks are:

Actor:

- 1 fully connected layer with 33 inputs and 128 outputs (fc1)
- 1 fully connected layer with 128 inputs and 128 outputs (fc2)
- 1 fully connected layer with 128 inputs and 4 outputs (fc3)
- 2 ReLU functions, to apply to fc1 and fc2 in the feed forward
- 1 batch normalization function, to reduce variance applying it to fc1
- 1 Tanh function, to apply to the final layer fc3

Critic:

- 1 fully connected layer with 33 inputs and 128 outputs (fc1)
- 1 fully connected layer with 132 inputs (128 + action size) and 128 outputs (fc2)
- 1 fully connected layer with 128 inputs and 1 output (fc3)
- 2 ReLU functions, to apply to fc1 and fc2 in the feed forward
- 1 batch normalization function, to reduce variance applying it to fc1

## Hyperparameters

The hyperparameters used in this implementation were:

- Buffer size: 10000
- Batch size: 128
- Gamma: 0.99
- TAU: 0.001
- Learning rate (actor): 0.0002
- Learning rate (critic): 0.0002
- Weight decay: 0 

## Observations

The agent was able to solve the environment in only 197 episodes, what demonstrates the power of this off-policy algorithm,
taking the most advantage of a single episode. Here we can see how the agent learnt in a graphical mode:

![DDPG training Performance plot](results.png)

## Next steps

I want to implement on-policy algorithms like PPO and TRPO to compare the results, because on-policy methods are supposed to be
better for environments where you can repeat the tasks in the environment as much as you want (like this).