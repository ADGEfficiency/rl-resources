## To start with for reinforcement learning

[Sutton & Barto - Reinforcement Learning: An Introduction - 2nd Edition](http://incompleteideas.net/book/the-book-2nd.html)
- the Holy Bible of reinforcement learning
- highly awaited second edition released in 2019

UCL Lectures - David Silver (Head of Reinforcement Learning at DeepMind) - [slides](https://github.com/ADGEfficiency/dsr_rl/tree/master/literature/silver_lectures) - [lecture videos](https://www.youtube.com/watch?v=2pWv7GOvuf0)
- David Silver is Head of reinforcement learning at DeepMind
- 10 lectures

Open AI Spinning Up in Deep Reinforcement Learning - [notes](https://spinningup.openai.com/en/latest/) - [lecture](https://www.youtube.com/watch?v=fdY7dt3ijgY)
- educational resources from Open AI

## To start with for machine learning

For neural networks - [Deep Learning - Ian Goodfellow, Yoshua Bengio and Aaron Courville](https://www.deeplearningbook.org/)

For everything else (linear models, random forests etc) 

- [Elements of Statistical Learning - Trevor Hastie, Robert Tibshirani and Jerome Friedman](https://web.stanford.edu/~hastie/Papers/ESLII.pdf)
- [Pattern Recognition and Machine Learning - Christopher M. Bishop](http://users.isr.ist.utl.pt/~wurmd/Livros/school/Bishop%20-%20Pattern%20Recognition%20And%20Machine%20Learning%20-%20Springer%20%202006.pdf)

## To get started coding

Start out building simple algorithms, progressing to more complex:

- dynamic programming
- cross entropy method
- DQN
- REINFORCE
- A2C
- PPO

Don't build an environment and agent at the same time!  You won't be sure where the problem is when debugging.

Part of the learning process is gaining familiarity with environments.  [Cartpole](https://gym.openai.com/envs/CartPole-v0/), [Pendulum](https://github.com/openai/gym/wiki/Pendulum-v0) and [Mountain Car](https://github.com/openai/gym/wiki/MountainCar-v0) are good basic environments.  Cartpole has a discrete action space, Pendulum a continuous action space and Mountain Car offers a challenging exploration problem.  [Open AI gym](https://github.com/openai/gym) has high quality implementations of these basic environments along with support for Atari and Mujocco.

## Videos & lectures

[The Long-term of AI & Temporal-Difference Learning (Richard Sutton - DeepMind)](https://www.youtube.com/watch?v=EeMCEQa85tw)

[Deep Reinforcement Learning (John Schulman - Open AI & Berkley)](https://www.youtube.com/watch?v=PtAIh9KSnjo)

[Deep Reinforcement Learning (Pieter Abbeel - Open AI & Berkley)](https://www.youtube.com/watch?v=ID150Tl-MMw)

[Deep Reinforcement Learning (David Silver - DeepMind & UCL)](https://www.youtube.com/watch?v=M5a6HasTHs4)

[Deep Reinforcement Learning and Real World Challenges (Raia Hadsell - DeepMind)](https://www.youtube.com/watch?v=0e_uGa7ic74)

[Deep Reinforcement Learning in TensorFlow (Danijar Hafner - Stanford)](http://web.stanford.edu/class/cs20si/lectures/slides_14.pdf)

[2017 NIPS David Silver Keynote - AlphaZero](https://www.youtube.com/watch?v=A3ekFcZ3KNw)

[ICML 2017: Test of Time Award (Sylvain Gelly & David Silver)](https://www.youtube.com/watch?v=Bm7zah_LrmE)

[A History of Reinforcement Learning - Prof. A.G. Barto](https://www.youtube.com/watch?v=ul6B2oFPNDM)

[Reproducibility, Reusability, & Robustness in Deep Reinforcement Learning - Prof. Pineaue](https://www.youtube.com/watch?v=-0G98MYUtjI)

[The Power of Self-Learning Systems - Demis Hassabis](https://www.youtube.com/watch?v=3N9phq_yZP0)

## Entire field overviews & courses

François-Lavet et. al (2018) An Introduction to Deep Reinforcement Learning - [paper](https://arxiv.org/pdf/1811.12560.pdf)

CS 294: Deep Reinforcement Learning, Fall 2017 - Sergey Levine - Berkley - [course materials](http://rail.eecs.berkeley.edu/deeprlcourse-fa17/index.html) - [lecture videos](https://www.youtube.com/playlist?list=PLkFD6_40KJIznC9CDbVTjAF2oyt8_VAe3)

CS 598: Statistical Reinforcement Learning - Nan Jiang - Illinois - [course materials](http://nanjiang.cs.illinois.edu/cs598/)

A (Long) Peek into Reinforcement Learning - [blog post](https://lilianweng.github.io/lil-log/2018/02/19/a-long-peek-into-reinforcement-learning.html)

Practical RL - course in reinforcement learning in the wild - [repo](https://github.com/yandexdataschool/Practical_RL)

## Deep RL Bootcamp lectures

2017 two day bootcamp hosted by Berkley

- [Lecture 1 - Motivation + Overview + Exact Solution Methods - Pieter Abbeel](https://www.youtube.com/watch?v=qaMdN6LS9rA)
- [Lecture 2 - Sampling-based Approximations and Function Fitting - Yan (Rocky) Duan](https://www.youtube.com/watch?v=qO-HUo0LsO4)
- [Lecture 3 - Deep Q-Networks - Vlad Mnih](https://www.youtube.com/watch?v=fevMOp5TDQs)
- [Lecture 4a - Policy Gradients - John Schulman](https://www.youtube.com/watch?v=S_gwYj1Q-44)
- [Lecture 4b - Policy Gradients Revisited - Andrej Karpathy](https://www.youtube.com/watch?v=tqrcjHuNdmQ)
- [Lecture 5 - Natural Policy Gradients, TRPO, PPO - John
Schulman](https://www.youtube.com/watch?v=tqrcjHuNdm://www.youtube.com/watch?v=xvRrgxcpaHY)
- [Lecture 6 - Nuts and Bolts of Deep RL Experimentation - John
Schulman](https://www.youtube.com/watch?v=8EcdaCk9KaQ)
- [Lecture 7 - SVG, DDPG, and Stochastic Computation Graphs - John Schulman](https://www.youtube.com/watch?v=jmMsNQ2eug4)
- [Lecture 8 - Derivative Free Methods - Xi (Peter) Chen](https://www.youtube.com/watch?v=SQtOI9jsrJ0)
- [Lecture 9 - Model-based Reinforcement Learning - Chelsea Finn](https://www.youtube.com/watch?v=iC2a7M9voYU)
- [Lecture 10a - Utlities - Pieter Abbeel](https://www.youtube.com/watch?v=yA6wXERug70)
- [Lecture 10b - Inverse Reinforcement Learning - Chelsea Finn](https://www.youtube.com/watch?v=d9DlQSJQAoI)
- [Frontiers Lecture I - Recent Advances, Frontiers and Future of Deep
RL - Vlad Mnih](https://www.youtube.com/watch?v=bsuvM1jO-4w&t=1s)- 
- [Frontiers Lecture II: Recent Advances, Frontiers and Future of Deep RL - Sergey Levine](https://www.youtube.com/watch?v=lYU5nq0dAQQ)

## Blog posts

[Deep Reinforcement Learning: Pong from Pixels](http://karpathy.github.io/2016/05/31/rl/)

[Deep Deterministic Policy Gradients in TensorFlow](http://pemami4911.github.io/blog/2016/08/21/ddpg-rl.html)

[Deep Reinforcement Learning Doesn't Work Yet](https://www.alexirpan.com/2018/02/14/rl-hard.html)

[Maximum Entropy Policies in Reinforcement Learning & Everyday Life](https://medium.com/@awjuliani/maximum-entropy-policies-in-reinforcement-learning-everyday-life-f5a1cc18d32d)

[AlphaGo, in context](https://medium.com/@karpathy/alphago-in-context-c47718cb95a5)

[World Models](https://worldmodels.github.io/)

## Code bases

Open AI gym - environments - [repo](https://github.com/openai/gym/tree/master/gym) - [paper](https://arxiv.org/abs/1606.01540)

Open AI baselines - agents - [repo](https://github.com/openai/baselines)

Berkley's rllab - agents & environments - [repo](https://github.com/rll/rllab)

Intel's coach - agents & environments - [repo](https://github.com/NervanaSystems/coach) - [blog post](https://ai.intel.com/introducing-reinforcement-learning-coach-0-10-0/)

unity - 3D environments - [github](https://github.com/Unity-Technologies/ml-agents) - [paper](https://arxiv.org/pdf/1809.02627.pdf)

Dopamine - Rainbow implementation - [github](https://github.com/google/dopamine) - [blog post](https://github.com/google/dopamine)

Holodeck - Unity 3D environments - [github](https://github.com/byu-pccl/holodeck-engine) - [blog post](https://pcc.cs.byu.edu/2018/10/04/introducing-holodeck/)

[Parallel Monte-Carlo tree search to tackle the problem of long-term path planning under uncertainty for offshore sailing](https://github.com/PBarde/IBoat-PMCTS)

[RLenv.directory](https://rlenv.directory/) - directory of reinforcement learning environments

Horizion - Facebook platform for applied RL - [github](https://github.com/facebookresearch/Horizon) - [paper](https://arxiv.org/abs/1811.00260) - [blog post](https://code.fb.com/ml-applications/horizon/)
