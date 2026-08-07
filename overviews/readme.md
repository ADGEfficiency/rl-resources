[What are the current state-of-the-art algorithms? : r/reinforcementlearning](https://www.reddit.com/r/reinforcementlearning/comments/10h4gms/what_are_the_current_stateoftheart_algorithms/)

In the DQN world it's probably: MEME (Human-level Atari 200x faster, Kapturowski et al., 2022)

The paper line I would follow to understand everything there is: DQN -> Rainbow -> R2D2 -> NeverGiveUp -> Agent57 -> MEME

---

DreamerV3 is definitely not simple and also computationally heavy. PPO for on-policy and SAC for off-policy are simple and don't need too much compute. Even though I would use TQC for off-policy. It improves quite a bit over SAC and isn't more expensive in terms of compute. 

[Exploration Strategies in Deep Reinforcement Learning | Lil'Log](https://lilianweng.github.io/posts/2020-06-07-exploration-drl/)

Open AI Spinning Up in Deep Reinforcement Learning - [notes](https://spinningup.openai.com/en/latest/) - [lecture](https://www.youtube.com/watch?v=fdY7dt3ijgY)

[ICML 2018: Tutorial Session: Optimization Perspectives on Learning to Control - Ben Recht](https://www.youtube.com/watch?v=hYw_qhLUE0o)

[An Outsider's Tour of Reinforcement Learning - Ben Recht](http://www.argmin.net/2018/06/25/outsider-rl/)

[Tutorial: Introduction to Reinforcement Learning with Function Approximation - Rich Sutton (youtube)](https://www.youtube.com/watch?v=Fsh1qMTg1xI)

[Deep Reinforcement Learning Doesn't Work Yet](https://www.alexirpan.com/2018/02/14/rl-hard.html)

[The Promise of Hierarchical Reinforcement Learning - The Gradient (blog post)](https://thegradient.pub/the-promise-of-hierarchical-reinforcement-learning/)

[The Long-term of AI & Temporal-Difference Learning (Richard Sutton - DeepMind)](https://www.youtube.com/watch?v=EeMCEQa85tw)

[Deep Reinforcement Learning (John Schulman - Open AI & Berkeley)](https://www.youtube.com/watch?v=PtAIh9KSnjo)

[Deep Reinforcement Learning (Pieter Abbeel - Open AI & Berkeley)](https://www.youtube.com/watch?v=ID150Tl-MMw)

[Deep Reinforcement Learning (David Silver - DeepMind & UCL)](https://www.youtube.com/watch?v=M5a6HasTHs4)

[Deep Reinforcement Learning and Real World Challenges (Raia Hadsell - DeepMind)](https://www.youtube.com/watch?v=0e_uGa7ic74)

[Deep Reinforcement Learning in TensorFlow (Danijar Hafner - Stanford)](http://web.stanford.edu/class/cs20si/lectures/slides_14.pdf)

[A History of Reinforcement Learning - Prof. A.G. Barto](https://www.youtube.com/watch?v=ul6B2oFPNDM)

[Reproducibility, Reusability, & Robustness in Deep Reinforcement Learning - Prof. Pineaue](https://www.youtube.com/watch?v=-0G98MYUtjI)

[The Power of Self-Learning Systems - Demis Hassabis](https://www.youtube.com/watch?v=3N9phq_yZP0)

[RL-Picker - Reinforcement-learning algorithm picker](https://rl-picker.github.io/)

## Fundamentals

<!-- From Sutton Introduction to RL, Second Edition -->

**Core definition**: Learning what to do to maximize a reward signal
- Map situations to actions
- Actions affect the future

Two most important features of reinforcement learning:
1. **Trial & error search**
2. **Delayed reward**

RL = computational approach to learning through action - the whole problem of goal-directed agent interaction with environment

Optimal control of incompletely known MDPs - framework from dynamical systems theory

Contrast with supervised learning:
- Want generalization
- Might not be able to get it if don't have examples of actions
- Uncharted territory is often the value part
- Explore/exploit only in RL

## Deep RL Framing

<!-- From Schulman & Abbeel Deep RL lectures -->

Deep RL = using neural networks as function approximators. Not obvious what to approximate (policy, value function, or a model of the env / dynamics model).

Applications: robotics, smart contracts, business operations (inventory management), sequential/structured prediction, recommendation systems. A stateful env means you need to take many actions to get into the right state = have to think ahead (not just greedy for the next time step).

**ML vs RL**: don't have access to the function you are trying to optimize, must query it through interaction with a stateful world (input to agent depends on previous actions). Deep RL won't work out of the box - lots of knobs to tune.

If the problem has a small number of parameters and you have a simulator, derivative-free optimization methods (simulated annealing, cross entropy method, SPSA) are likely to be better and will work out of the box. Operations research has a well-developed set of feature-engineering techniques for these problems.

**MDP formalism**: maximize expected cumulative reward. Episodic setting = act until terminal state. Policy = function used to determine actions - stochastic (a conditional probability distribution) or deterministic. For a discrete action space the policy network outputs a vector of probabilities; for continuous, it outputs the mean and diagonal covariance of a Gaussian (essentially regression).

**Fundamentals (Sutton & Barto)**

Core definition: learning what to do to maximize a reward signal - map situations to actions, where actions affect the future

Two most important features of reinforcement learning:
1. Trial & error search
2. Delayed reward

RL = optimal control of incompletely known MDPs - framework from dynamical systems theory

Contrast with supervised learning - might not have examples of actions, and uncharted territory is often the valuable part. Explore/exploit only exists in RL
