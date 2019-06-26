[Tutorial: Introduction to Reinforcement Learning with Function Approximation - Decemberr 2015 - Rich Sutton](https://www.youtube.com/watch?v=Fsh1qMTg1xI)

[Reinforcement Learning on Hundreds of Thousands of Cores - Henrique Ponde de Oliveira Pinto - Open AI](https://www.youtube.com/watch?v=ui4F_A46wN0) - scaling the Open AI DOTA agents

DOTA
- co-ordination
- imperfect info

180 years of games per day

100,000x CPU playing the game

100x GPU learning

These needs to be connected with a controller (Redis)
- this holds the configs & parameters
- single source of truth
- can easily backup to disk

Use Lua scripts inside Redis

