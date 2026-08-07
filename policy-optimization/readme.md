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

## Off-Policy Training

Value-Based methods such as DQN, C51, Rainbow DQN can naturally be trained off-policy using a Replay Buffer, without having to account for any kind of off-policy correction.

Deterministic Policy Gradient methods, such as DDPG or TD3 can be trained off-policy, as they don't integrate over actions.

Stochastic Policy Gradient methods can't, on principle, be trained off-policy, as they need to estimate the gradient using the current policy. However using importance sampling, you can correct that off-policiness, eg the way TRPO, ACER does.

Importance sampling used to correct for small delays. PPO does multiple steps for each rollout, and needs to use IS to correct for slight drift from being on policy. Importance weights can explode/shrink/be unstable for pure off-policy learning. You need the prob for the action under your policy.

DDPG is a continuous adaptation of Q-Learning - no argmax, this gives you the freedom from being on policy, but rather a policy that approximates the argmax for the continuous Q net.

## PPO Practical Tips

**Finding nans**: try clipping everywhere you divide by and adding `assert ~np.isnan(value.data.cpu().numpy())` in a few places to narrow down NaN's. `logprob.clamp(log(1e-7), -log(1e-7))`.

**Exploration using a parameterized standard deviation**: using the network to output the std dev can lead to huge instabilities, try using a single trainable parameter for it.

**General**: if it doesn't work, try increasing the batch size. No problem using the full episode to update, but be sure to train for multiple epochs on the same trajectory (that's what PPO is for). For the value network, consider dividing it in mini-batches.

## Policy Gradient Mechanics

<!-- From Schulman & Abbeel Deep RL lectures -->

We want to make good trajectories more probable, or make good actions more probable, or push actions towards better actions (DPG, SVG).

**Score function gradient estimator**: to compute the gradient of $E[f(x)]$, use $E[f(x) \cdot \nabla \log p(x)]$ - an unbiased sample of the gradient. Need to compute the probability density and differentiate wrt policy parameters (can also derive via importance sampling). Pushes up the log-prob of a sample in proportion to how good it is. Valid even if $f(x)$ is discontinuous, unknown, or the sample space is discrete - you only need to query it.

Abbeel: likelihood-ratio PG doesn't need a dynamics model. Increase probability of paths with positive R, decrease for negative R. It only changes the probability of experienced paths, not the paths themselves. A stochastic policy smooths out the optimization landscape and starts high-entropy, decreasing over time.

### Variance Reduction

Only look at future rewards (not total reward) - reduces variance. **Introducing a baseline** reduces variance: `sum(future rewards) - baseline(state)`, which doesn't change the expectation (still unbiased). Advantage estimate = $Q(s,a) - v(s)$ (how much better this action is than the average action for this policy).

### Trust Region Policy Optimization (TRPO)

Step sizes matter more than in supervised learning: a step too far in RL can give a bad policy, and the next batch is collected under that bad policy (hard to recover). TRPO keeps the KL divergence between policy updates bounded. Using value functions for further variance reduction introduces bias - more data drives variance down but won't fix a biased (wrong-direction) gradient.

### Q-Learning vs Policy Gradients

Q-learning can be applied to continuous state/action with expressive function approximators, but it's harder to know when it will work. Q is more sample-efficient *when it works*; otherwise PG converges better because it optimizes what you care about directly (Q learns Q and hopes it gives a good policy). Reliability & robustness is the first consideration.

Design considerations: reward-signal design vs amount of exploration required; quantization of space & time (the time step matters). Too small a time step → delayed rewards (harder credit assignment) and random-walk-like exploration.

## Policy Optimization Algorithms

[NIPS 2016 - Deep RL Through Policy Optimization - Schulman & Abbeel](https://people.eecs.berkeley.edu/~pabbeel/nips-tutorial-policy-optimization-Schulman-Abbeel.pdf)

[It's Only Natural: An Excessively Deep Dive Into Natural Gradient Optimization](https://towardsdatascience.com/its-only-natural-an-excessively-deep-dive-into-natural-gradient-optimization-75d464b89dbb)

[Beyond DQN/A3C: A Survey in Advanced Reinforcement Learning](https://towardsdatascience.com/advanced-reinforcement-learning-6d769f529eb3)

[OpenAI Baselines: ACKTR & A2C](https://openai.com/blog/baselines-acktr-a2c/)

Two costs matter: sample complexity (timesteps of agent-env interaction) and computational complexity (numerical operations). **ACKTR** gets better sample complexity using the natural gradient - the direction in parameter space giving the largest improvement per unit change in the network's output distribution (measured by KL divergence). Limiting the KL divergence ensures the new policy doesn't behave radically differently, which could collapse performance.
