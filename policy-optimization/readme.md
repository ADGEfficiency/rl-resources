[ayushdnb/Tensor-Crypt](https://github.com/ayushdnb/Tensor-Crypt) - Tensor-backed multi-agent simulation runtime with a pygame-ce viewer, UID-owned PPO training state, structured telemetry, and atomic checkpoint publication.

[The 37 Implementation Details of Proximal Policy Optimization](https://iclr-blog-track.github.io/2022/03/25/ppo-implementation-details/)

[vwxyzjn/ppo-implementation-details](https://github.com/vwxyzjn/ppo-implementation-details) - The source code for the blog post The 37 Implementation Details of Proximal Policy Optimization

[Deep Reinforcement Learning: Pong from Pixels](http://karpathy.github.io/2016/05/31/rl/)

[Deep Deterministic Policy Gradients in TensorFlow](http://pemami4911.github.io/blog/2016/08/21/ddpg-rl.html)

[ppocma/ppocma](https://github.com/ppocma/ppocma) - [paper](https://arxiv.org/abs/1810.02541)

The Pursuit of (Robotic) Happiness: How TRPO and PPO Stabilize Policy Gradient Methods - [blog-post](https://towardsdatascience.com/the-pursuit-of-robotic-happiness-how-trpo-and-ppo-stabilize-policy-gradient-methods-545784094e3b)

[What's After PPO? : r/reinforcementlearning](https://www.reddit.com/r/reinforcementlearning/comments/1gqr1k3/whats_after_ppo/?share_id=85HyEW9lRvwiUnU2IGpMF&utm_name=androidcss)

Phasic policy gradients is a really cool idea and not too hard to implement, but myself and colleagues have experimentally found it to perform no better than vanilla ppo on many environments.

Truly PPO is considered a more correct version of PPO but the performance is basically the same.

Ewma PPO (batch size invariance for policy optimisation) is a great paper that's not too hard to implement and helps PPO deal with learning from off-policy data better.

Impala, which is essentially distributed recurrent PPO with a built in off-policy correction mechanism (v-trace). It was used in AlphaStar and OpenAIFive and is a solid go to algorithm.

Discovered policy optimisation is an excellent paper where a pure JAX PPO meta RL setup discovered a better objective function than vanilla PPO that let it learn much faster. This is probably the biggest improvement to vanilla ppo that doesn't require any new parts if you just take the better objective function.

MAPPO is PPO that uses a centralised critic in a multi-agent setting, using the centralised training decentralised execution paradigm. It's among the strongest of the MARL algos (source: The Surprising Effectiveness of PPO in Cooperative, Multi-Agent Games).

What matters in on-policy reinforcement learning is an excellent paper for PPO implementation tweaks.

There are many other algorithms worth learning other than PPO obviously but these are all PPO-related suggestions.

[Data 2 with Large Scale Deep Reinforcement Learning](https://cdn.openai.com/dota-2.pdf)

In order to train without restarting from the beginning after each change, we developed a collection of tools to resume training with minimal loss in performance which we call surgery.

Over the 10-month training process, we performed approximately one surgery per two weeks.

These tools allowed us to make frequent improvements to our strongest agent within a shorter time than the typical practice of training from scratch would allow

---

These changes can modify the shapes and sizes of the model’s layers, the semantic meaning of categorical observation values, etc.

Surgery = collection of tools to perform operations to the old model
