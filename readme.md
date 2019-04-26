This repository is my personal collection of reinforcement learning resources.  If you like this check out my [reinforcement learning course](https://github.com/ADGEfficiency/rl-course) and [ml-resources](https://github.com/ADGEfficiency/ml-resources) repos.

Most of the content is spread into subject specific folders such as `alphago` and `model-based`.  Below is some advice aimed at those new to reinforcement learning.

## Textbooks and courses

[Sutton & Barto - Reinforcement Learning: An Introduction - 2nd Edition](http://incompleteideas.net/book/the-book-2nd.html) - highly awaited second edition released in 2019

UCL Lectures - David Silver (Head of Reinforcement Learning at DeepMind) - [slides](https://github.com/ADGEfficiency/dsr_rl/tree/master/literature/silver_lectures) - [10 lecture videos](https://www.youtube.com/watch?v=2pWv7GOvuf0)

Open AI Spinning Up in Deep Reinforcement Learning - [notes](https://spinningup.openai.com/en/latest/) - [lecture](https://www.youtube.com/watch?v=fdY7dt3ijgY)

## Start coding

To train a reinforcement learning agent you need three things - an environment ([look at Open AI gym](https://github.com/openai/gym)), an agent and code to run the experiments.

Start out building simple agents and code to run experiments.  A list of agents to work through is given below:

- dynamic programming
- cross entropy method
- DQN
- REINFORCE
- A2C
- PPO

Don't build an environment and agent at the same time!  You won't be sure where the problem is when debugging.  Run experiments over multiple random seeds, and expect to see variance in learning across different random seeds.

Part of the learning process is gaining familiarity with how quickly an agent should learn on a toy environment.  Three useful environments are:
- [Cartpole](https://gym.openai.com/envs/CartPole-v0/) - discrete action space
- [Pendulum](https://gym.openai.com/envs/Pendulum-v0/) - continuous action space
- [MountainCar](https://gym.openai.com/envs/MountainCar-v0/) - difficult exploration problem
