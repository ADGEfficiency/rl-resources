[Modeling for Reinforcement Learning and Optimal Control: Double pendulum on a cart (blog post)](https://medium.com/@JonasCoen/modeling-for-reinforcement-learning-and-optimal-control-double-pendulum-on-a-cart-394f46b7ec7e?sk=b1d33aada3cf45844142563a3044b8c2)

Google Brain SimPLe: Complete Model-Based Reinforcement Learning for Atari 
- [Synced blog post](https://medium.com/syncedreview/google-brain-simple-complete-model-based-reinforcement-learning-for-atari-b350a960921c)

[When to Trust Your Model: Model-Based Policy Optimization](https://people.eecs.berkeley.edu/~janner/mbpo/)

## Machines that learn by doing - Sergey Levine - [youtube](https://www.youtube.com/watch?v=yLHzDky2ApI)

Intelligent machines must adapt to the physicality, complexity and messiness of the real world - in ML this is generalization. RL = a formalism for behaviour. Deep RL has succeeded in domains *unlike* the real world (Go is structured, with few unexpected situations). It's not about deep nets - it's about big models + highly varied, diverse data (the lesson from supervised learning).

**On-policy vs off-policy**: on-policy RL collects data, learns, then throws it away - only works if the inner loop is simulation. Off-policy RL uses a big dataset to learn the diversity of the real world and allows reuse of data; it is a prediction problem (rewards = value functions, observations = model based).

**Why not Q-learning?** Q-learning with nonlinear function approximation isn't guaranteed to converge in theory or practice, is sensitive to hyperparameters, and has many local optima - you can force convergence by torturing hyperparameters. Sample complexity varies wildly (Pong = 2M–10M frames, sometimes many more). Algorithms vary in how off-policy they can be, and it's hard to know how much of an issue that is. Expect variance across random seeds.

**Generalization from real-world experience**: RL tasks are small, uniform, goal = master, test identical to train. The real world is huge, highly varied, goal = don't screw up too much, test set = an unmitigated disaster of complexity. Off-policy RL learns from diverse datasets. Can we go further and learn something about physics?

**Model-based as semi-supervised learning**: (1) play with objects in the real world, (2) use this data to train a predictive model conditioned on $(s, a)$.



