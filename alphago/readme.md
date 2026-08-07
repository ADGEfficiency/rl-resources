<a style="font-size: 1rem;" href="https://en.wikipedia.org/wiki/Deep_Blue_(chess_computer)">Deep Blue - Wikipedia</a>

<a style="font-size: 1rem;" href="https://en.wikipedia.org/wiki/AlphaGo">Alpha Go - Wikipedia</a>

AlphaZero - Mastering Games Without Human Knowledge - David Silver - [youtube](https://www.youtube.com/watch?v=Wujy7OzvdJk)

[AlphaGo Zero: Learning from scratch - DeepMind (blog post)](https://deepmind.com/blog/alphago-zero-learning-scratch/)

[AlphaGo, in context](https://medium.com/@karpathy/alphago-in-context-c47718cb95a5)

[2017 NIPS David Silver Keynote - AlphaZero](https://www.youtube.com/watch?v=A3ekFcZ3KNw)

[ICML 2017: Test of Time Award (Sylvain Gelly & David Silver)](https://www.youtube.com/watch?v=Bm7zah_LrmE)

[The Power of Self-Learning Systems - Demis Hassabis](https://www.youtube.com/watch?v=3N9phq_yZP0)

[AlphaStar: Mastering the Game of StarCraft II ](https://slideslive.com/38917653/alphastar-mastering-the-game-of-starcraft-ii)

[[2211.00241] Adversarial Policies Beat Superhuman Go AIs](https://arxiv.org/abs/2211.00241)

Magnus Carlsen using uncommon openings to push opponents into unfamiliar territory

## Go vs Chess

**Chess**: branch = 40, depth = 80 steps, possible to evaluate positions by summing piece values

**Go**: branch = 100, steps = 100-300, difficulty evaluating positions (same number of stones), have model, can simulate, test performance

## MoGo (2007)

<!-- From ICML 2017 Test of Time (Gelly & Silver) -->

In 2007, RL at beginner level, alpha/beta search was state of the art.

Used shape features to look for patterns of stones (value of 1 if pattern appears, take linear combination of the patterns). Uses TD($\lambda$) plus handcrafted knowledge. Initialized the MC tree values using the value function - this became state of the art.

Also tried a policy with a softmax over states as the rollout policy - stronger offline policy didn't lead to an effective rollout policy (diversity was lost using a greedy policy). Future work used supervised learning due to the diversity in human moves.

MoGo (2007) = MCTS + RAVE + simple value function + rollouts w/ custom policy - 99% win versus traditional programs, first victory against pro player (9x9). Most improvements since 2007 on the offline (better features + learning from human data). Plateau in performance 2012-2017.

## AlphaGo

12 layers in original network (many more now). Improved policy using policy gradient techniques. Value function predicts who will win from games of self-play. Reduce depth with value network, reduce width with policy. Backing up the value function throughout the entire search tree (rather than just affecting one value). RAVE not helpful in AlphaGo.

AlphaGo two big changes:
- Deep learning
- More effective way to combine on + offline knowledge

UCT in AlphaGo Lee & Zero:

$$UCT(v_i, v) = \frac{Q(v_i)}{N(v_i)} + cP(v, v_i) \sqrt{\frac{N(v)}{1+N(v_i)}}$$

$P(v_i,v)$ = prior probability of move based on policy network. SL policy net used (rather than RL policy net) as it performs better in practice - maybe because humans give a better exploration. $c$ = hyperparameter to tune between exploration and exploitation.

In Alpha Zero - multiple versions of the network trained in parallel. At each checkpoint, best one is chosen for training data generation by evaluation against best current.

AlphaGo uses combination of MCTS rollouts with the value network. Alpha Zero doesn't use playouts - just directly evaluates nodes using resnet.
