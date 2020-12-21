[Tutorial: Introduction to Reinforcement Learning with Function Approximation - Decemberr 2015 - Rich Sutton](https://www.youtube.com/watch?v=Fsh1qMTg1xI)

[On The Hardness of Reinforcement Learning With Value-Function Approximation](https://www.youtube.com/watch?v=SjO386Mksa0)

[Building Reproducible, Reusable and Robust Deep RL Systems - Joelle Pineau](https://www.youtube.com/watch?v=Phy9Yex5bm4&list=WL&index=10)

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

[Tutorial: Introduction to Reinforcement Learning with Function Approximation](https://www.youtube.com/watch?v=Fsh1qMTg1xI)

*1:21:30*

What causes instability?

Not learning / sampling
- DP diverges (w/ function approx)

Not exploration
- policy evaluation can diverge

Not non-linear functions
- linear functions can diverge

Risk of divergence occurs when combining
1. function approximation
2. bootstrapping
3. off policy learning

Any two are OK - three not

Can we remove bootstrapping?
- key to computational/data efficiency
- introduces bias

*1:28:25*


