This repository is my personal collection of reinforcement learning resources.  If you like this check out my [reinforcement learning course](https://github.com/ADGEfficiency/rl-course) and [ml-resources](https://github.com/ADGEfficiency/ml-resources) repos.

## If you are starting out with reinforcement learning

[Sutton & Barto - Reinforcement Learning: An Introduction - 2nd Edition](http://incompleteideas.net/book/the-book-2nd.html)
- the Holy Bible of reinforcement learning
- highly awaited second edition released in 2019

UCL Lectures - David Silver (Head of Reinforcement Learning at DeepMind) - [slides](https://github.com/ADGEfficiency/dsr_rl/tree/master/literature/silver_lectures) - [lecture videos](https://www.youtube.com/watch?v=2pWv7GOvuf0)
- David Silver is Head of reinforcement learning at DeepMind
- 10 lectures

Open AI Spinning Up in Deep Reinforcement Learning - [notes](https://spinningup.openai.com/en/latest/) - [lecture](https://www.youtube.com/watch?v=fdY7dt3ijgY)
- educational resources from Open AI

## To get started building reinforcement learning programs

Start out building simple algorithms, progressing to more complex

- dynamic programming
- cross entropy method
- DQN
- REINFORCE
- A2C
- PPO

Don't build an environment and agent at the same time!  You won't be sure where the problem is when debugging.

Part of the learning process is gaining familiarity with environments.  [Cartpole](https://gym.openai.com/envs/CartPole-v0/), [Pendulum](https://github.com/openai/gym/wiki/Pendulum-v0) and [Mountain Car](https://github.com/openai/gym/wiki/MountainCar-v0) are good basic environments.  Cartpole has a discrete action space, Pendulum a continuous action space and Mountain Car offers a challenging exploration problem.  [Open AI gym](https://github.com/openai/gym) has high quality implementations of these basic environments along with support for Atari and Mujocco.

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
