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

[RL - Hidden Theory and New Super Fast Algorithms](https://www.youtube.com/watch?v=dhEF5pfYmvc)

Monte Carlo = find mean of a function of a random variable

Doesn't believe that black box learning for control is real - believes in building simulators. If you don't know f or W = model free rl. Q-learning slow - for discount factor > 0.5, variance is infinity. Stochastic approx = gets rid of this expectation.

[Sample-Efficient Reinforcement Learning with Rich Observations](https://www.youtube.com/watch?v=L5Q4Y3omnrY) - [slides](https://simons.berkeley.edu/sites/default/files/docs/6268/cdp-berkeley.pdf)

Practice = powerful models, simple exploration. Theory = sophisticated exploration in simple MDPs ($E^3$, R-MAX), limited theory for rich observations.

Goal = RL approaches that work with small number of samples but rich observations.

Bellman Rank - measure for the hardness of exploration. Consistency checks that optimal Bellman equations have to satisfy (TD error is zero for all states in a rollout). Pick the value function that says it will give the most reward, then check using the TD error on a few rollouts, rejecting any value functions that fail some condition. Optimism Led Iterative Value-function Elimination (OLIVE).

[Reproducibility, Reusability, & Robustness in Deep Reinforcement Learning - Prof. Pineau](https://www.youtube.com/watch?v=-0G98MYUtjI)

Article = advertising. The scholarship itself is the software development environment that generated the figures. Reusable material → helps to reproduce results → more robustness of the findings.

Show that different implementations of the same algo (TRPO) give massively different results. Not doing enough rollouts, taken top 3 results → positive bias + small variance. Same TRPO code giving two different results for 2x5 rollouts - variance across only random seeds.

Deep Reinforcement Learning (David Silver) - [slides](http://www0.cs.ucl.ac.uk/staff/d.silver/web/Talks_files/deep_rl.pdf)

Deep learning = compositions of functions. Weight sharing in deep learning (reusing kernels over whole image + recurrent sharing over time). SGD gets us close enough - empirical and some theoretical evidence that our intuitions about optimization in high dim spaces were incorrect - a local opt is pretty close to global. Sensitive to parameter initialization.

[A History of Reinforcement Learning - Prof. A.G. Barto](https://www.youtube.com/watch?v=ul6B2oFPNDM)

Hedonistic neuron hypothesis - Harry Klopf - neurons work to maximize local pleasure and minimize local pain

**Supervised** = learning with a teacher from error vectors

**Reinforcement** = learning with a critic - doesn't provide a gradient. Critic doesn't see the output of the learner - bases its evaluation on some distal consequence of the learner, through some unmodelled system. This is a very important property of RL.

Roots go back to **Edward Thorndike** (1874-1949) - learning through trial and error.

**RL = search + memory**
- Search: trial + error, generate + test, variation + selection
- Memory: remember what worked best for each situation and start from there

RL = caching search results (so you don't have to keep searching) - memoized contextual search. Trial + error != error correction.

Influenced by John Holland's genetic algorithms + associative memory networks → **associative search networks (1981)** (contextual search). Noise in the network drove search. Led to **actor critic (1983)** - actor + adaptive critic. Rich Sutton's thesis → **TD algorithms**.

**Arthur Samuel's checkers player** (1959) = important connection; TD is an improvement on this. Another connection = **dynamic programming** + optimal control (DP in 1953). Samuel + Bellman never talked to each other. RL bridges the silo. DP was dismissed as 'breadth first' - it is, but it is memoized, which is key.

**TD Gammon** (early 1990's) - multilayer network + Monte Carlo. Used MC to beat the curse of dimensionality (10^20 states - one sweep of DP would take 10-20 years). RL is slow, but has advantage compared with classical DP.

Modern era challenge = **designing reward functions**. Be careful what you wish for. Idea of 'corrigibility' - humans must be able to change the reward signal.

Hedonistic neuron hypothesis (Harry Klopf) - neurons work to maximize local pleasure and minimize local pain

**Supervised** = learning with a teacher from error vectors. **Reinforcement** = learning with a critic - doesn't provide a gradient. The critic doesn't see the output of the learner - it bases its evaluation on some distal consequence of the learner, through some unmodelled system

Roots go back to Edward Thorndike (1874-1949) - learning through trial and error

**RL = search + memory**. Search = trial + error / generate + test / variation + selection. Memory = remember what worked best for each situation and start from there. RL = caching search results - memoized contextual search

Trial + error != error correction

Associative search networks (1981) → actor critic (1983) - actor + adaptive critic. Rich Sutton's thesis → TD algorithms. Arthur Samuel's checkers player (1959) - TD is an improvement on this. Samuel + Bellman never talked to each other / were aware of each other's work - RL bridges the silo between these disciplines. DP was dismissed as 'breadth first' - it is, but it is memoized, which is key

TD Gammon (early 1990s) - multilayer network + Monte Carlo to beat the curse of dimensionality. 10^20 states - one sweep of DP would take 10-20 years. MC control focuses computation onto relevant states - RL is slow, but has this advantage over classical DP

Modern challenge - designing reward functions: be careful what you wish for, you might just get it. Corrigibility - humans must be able to change the reward signal

[RL - Hidden Theory and New Super Fast Algorithms](https://www.youtube.com/watch?v=dhEF5pfYmvc)

Doesn't believe that black box learning for control is real - believes in building simulators. If you don't know f or W = model free RL

Q-learning slow - for discount factor > 0.5, variance is infinity. Stochastic approximation gets rid of this expectation

[Sample-Efficient Reinforcement Learning with Rich Observations](https://www.youtube.com/watch?v=L5Q4Y3omnrY) - [slides](https://simons.berkeley.edu/sites/default/files/docs/6268/cdp-berkeley.pdf)

Practice = powerful models, simple exploration. Theory = sophisticated exploration in simple MDPs ($E^3$, R-MAX), limited theory for rich observations

Bellman Rank - measure for the hardness of exploration. Pick the value function that says it will give us the most reward, then check using the TD error on a few rollouts, rejecting any value functions that fail - Optimism Led Iterative Value-function Elimination (OLIVE)

[Reproducibility, Reusability, & Robustness in Deep Reinforcement Learning - Prof. Pineau](https://www.youtube.com/watch?v=-0G98MYUtjI)

The article = advertising. The scholarship itself is the software development environment that generated the figures. Reusable material → helps to reproduce results → more robustness of the findings

Different algorithms perform differently on similar type problems. Different implementations of the same algorithm (TRPO) give massively different results. Same TRPO code gives two different results for 2x5 rollouts - variance across only random seeds

Not doing enough rollouts and taking top 3 results → positive bias + small variance

[Deep Reinforcement Learning (David Silver) - slides](http://www0.cs.ucl.ac.uk/staff/d.silver/web/Talks_files/deep_rl.pdf)

Weight sharing in deep learning - reusing kernels over the whole image + recurrent sharing over time

SGD gets us close enough - empirical and some theoretical evidence that our intuitions about optimization in high dimensional spaces were incorrect - a local optimum is pretty close to global. Sensitive to parameter initialization


