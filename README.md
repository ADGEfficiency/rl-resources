# Reinforcement Learning Resources

My personal collection of reinforcement learning resources.  

Most of the content is in subject folders such as `alphago` and `model-based`. 

## Textbooks and Courses

[Sutton & Barto - Reinforcement Learning: An Introduction - 2nd Edition](http://incompleteideas.net/book/the-book-2nd.html) - highly awaited second edition released in 2019

UCL Lectures - David Silver (Head of Reinforcement Learning at DeepMind) - [slides](https://github.com/ADGEfficiency/rl-resources/tree/master/courses/Silver-UCL-lectures) - [10 lecture videos](https://www.youtube.com/watch?v=2pWv7GOvuf0)

Open AI Spinning Up in Deep Reinforcement Learning - [notes](https://spinningup.openai.com/en/latest/) - [lecture](https://www.youtube.com/watch?v=fdY7dt3ijgY)

[Reinforcement Learning: A Six Part Series](https://youtu.be/NFo9v_yKQXA) (by Mutual Information)

## Getting Started Coding

To train a reinforcement learning agent you need three things - an environment ([look at Open AI gym](https://gym.openai.com/)), an agent and code to run the experiments.

Part of learning how to use reinforcement learning is gaining familiarity with how quickly an agent should learn on a toy environment.  

Three useful environments are:

- [Cartpole](https://gym.openai.com/envs/CartPole-v0/) - discrete action space
- [Pendulum](https://gym.openai.com/envs/Pendulum-v0/) - continuous action space
- [MountainCar](https://gym.openai.com/envs/MountainCar-v0/) - difficult exploration problem

Start out building simple agents and code to run experiments.  A list of agents to work through is given below:

- dynamic programming or value/policy iteration,
- cross entropy method (optional),
- REINFORCE,
- DQN,
- PPO,
- SAC.

Hints:

- **Don't make the common mistake of building an environment and agent at the same time!**  You won't be sure where the problem is when debugging.  
- **Run experiments over multiple random seeds** - expect to see variance in learning across only these random seeds.
- **Reinforcement learning is sample inefficient** - especially when all experiments need to be done across at least 3 random seeds.


## More Resources

If you like this check out:

- [ml-resources](https://github.com/ADGEfficiency/ml-resources), 
- [programming resources](https://github.com/ADGEfficiency/programming-resources),
- [rl-course](https://github.com/ADGEfficiency/rl-course).
