# Monte Carlo Tree Search

Monte Carlo = classic way to deal with difficult probability distributions

Monte Carlo = find mean of a function of a random variable

## Fundamentals

Monte Carlo Tree Search – beginners guide - [blog post](https://int8.io/monte-carlo-tree-search-beginners-guide/)

Introduced in 2006 (Remi Coulom). MCTS maps game state to action.

Branching factor = number of children of a node

Often in practice, you do not have to remember the path leading to your current state, as it is not a concern in a current game state.

## Minimax

$$V_A(s_i) = \underset{a_i}{max} v_B (move(s_i, a_i)) V_A(\hat{s} = eval(\hat{s})$$

$$V_B(s_i) = \underset{a_i}{max} v_A (move(s_i, a_i)) V_B(\hat{s} = -eval(\hat{s})$$

$eval$ = evaluates the final game state (at terminal node)

$\hat{s}$ = terminal state

In state $s$ - you want find a move $a_i$ that will result in the biggest reward assuming your opponent is trying minimize your reward. But we need to expand the entire tree - and backprop the value wrt the reward.

The big weakness of minimax is needing to fully expand the game tree. Possible remedy:
- Only expand the tree to a certain depth, and using some function to evaluate non-terminal states
- Alpha-beta pruning - avoids expanding some tree branches

## Online Learning

Spend compute resources on making a decision for a particular state = allows focus

Monte Carlo tree search = policy improvement by building a search tree

Remember the online values - use this to improve

Example of MCTS on a fixed rollout policy (uniform random) + greedy tree

Idea that you need to have some exploration in the tree

Expand the tree downwards - each node keeps a value

## Upper Confidence Bound for Trees (UCT)

UCT = upper confidence bound for tree = exploration of the tree
- Take the node that has the highest value
- Plus a exploration term that encourages actions

$$ V(s,a) + c \sqrt{ \frac{\log N(s)}{N(s,a)} } $$

$N(s)$ = sum for all actions

UCT = lets us choose next node among visited nodes

$$UCT(v_i, v) = \frac{Q(v_i)}{N(v_i)} + c \sqrt{\frac{\log(N(v))}{N(v_i)}}$$

The node that maximizes UCT is the one to follow

UCT = sum of a exploitation component and an exploration component.

## MCTS Algorithm

Search = down the game tree

Single traversal = path from root node (current state) to a node that is not fully expanded (ie one child state has not been visited).

When a non-fully expanded node is encountered, one of the unvisited children is chosen as root node and expanded for a single roll out.

During a roll out, a roll out policy is used - default is uniform random.

In MCTS, simulation starts at the node that has not been visited previously

A node is visited if a rollout is **started** in that node (evaluated at least once). Nodes chosen during the rollouts are not considered visited.

Node == leaf

## Backpropagation

Once a rollout is done (to terminal state) - start node is marked as visited

Backprop occurs from the leaf to the root! Not from the terminal state. The statistics of each node will reflect results of simulation started in all of its descendants.

## Statistics

Backprop wants to update total simulation reward $Q(v)$ and total number of visits $N(v)$ for all nodes on backprop path

These stats reflect how good a node is and how often it has been explored

## Going from root node to leaf

At beginning of search, unvisited nodes are chosen first. A single simulation starts at each, results are backproped and then root is considered fully expanded

In competitive games, the exploitation component is opposite for consecutive turns

## Terminating MCTS

Constrained by compute + efficiency

Best move is usually the one with highest number of visits - value has been well estimated (many visits) + high value (as it has been explored a lot)

Statistics from previous MCTS might be useful - this is done in alphago & zero

## Implementation

```python
def monte_carlo_tree_search(root):
    while resources_left(time, computational power):
        leaf = traverse(root) # leaf = unvisited node
        simulation_result = rollout(leaf)
        backpropagate(leaf, simulation_result)
    return best_child(root)

def traverse(node):
    while fully_expanded(node):
        node = best_uct(node)
    return pick_univisted(node.children) or node # in case no children are present / node is terminal

def rollout(node):
    while non_terminal(node):
        node = rollout_policy(node)
    return result(node)

def rollout_policy(node):
    return pick_random(node.children)

def backpropagate(node, result):
   if is_root(node) return
   node.stats = update_stats(node, result)
   backpropagate(node.parent)

def best_child(node):
    pick child with highest number of visits
```

Implementation of basic Monte Carlo Tree Search algorithm for Tic Tac Toe - [GitHub](https://github.com/int8/monte-carlo-tree-search)

## Offline vs Online Knowledge

No generalizing for a table

Monte Carlo estimate is high variance

Rapid Value Action Estimate (RAVE):
- Looking at the games where you play the same states
- Rather than looking at the result in a single rollout

**Offline knowledge**:

Value function and policy - these are offline because it's not specific to a single state

Need an estimate for the entire space
