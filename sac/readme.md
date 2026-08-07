Paper codebase - https://github.com/rail-berkeley/softlearning

Paper - https://arxiv.org/abs/1801.01290

Spinning Up SAC - https://spinningup.openai.com/en/latest/algorithms/sac.html

Haarnoja et al. (2019) Soft Actor-Critic Algorithms and Applications - https://arxiv.org/abs/1812.05905v2

softlearning - https://github.com/rail-berkeley/softlearning/blob/master/softlearning/algorithms/sac.py

## Maximum Entropy RL

[Maximum Entropy Policies in Reinforcement Learning & Everyday Life](https://medium.com/@awjuliani/maximum-entropy-policies-in-reinforcement-learning-everyday-life-f5a1cc18d32d)

Entropy = quantifies randomness / measures information / unpredictability of the actions taken in a given policy

```
entropy = - sum p(x) * log p(x)
```

Learning will lead to entropy decreasing - less random than the initial policy. Entropy bonus encourages more unpredictable actions. This is usually a one-step bonus (greedy optimization of entropy). Used in A3C & PPO.

Research now into long term entropy - actions that will maximize future entropy, not just current entropy - known as 'maximum entropy RL'. This optimizes for long term adaptability.

> In maximum entropy RL, the basic principle is that optimal behavior corresponds to a proper balance between commitment and adaptability.

Making sure that your life choices don't shut down options - not just plan for a good outcome, but for the ability to change when the world does.

## Soft Q-Learning

<!-- From Levine "Machines that learn by doing" -->

Stochastic energy-based policies - commit to the policy in proportion to the exponential of Q. A problem for continuous action spaces, which can be complex and multimodal. This is the max over rewards plus an entropy maximization - get a good policy with the most random policy possible.

Improves robustness in the face of unexpected perturbations, gives better exploration and more stable learning. Because the algorithm must deal with randomness during training, it yields a robust policy: using the worst random seed for a soft actor-critic still gives good stability across seeds, whereas DDPG has high-variance runs.
