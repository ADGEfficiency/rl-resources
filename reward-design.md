# Reward Function Design

Writing Great Reward Functions - Bonsai - [youtube](https://www.youtube.com/watch?v=0R3PnJEisqk)

Reward function $R(r|s,a)$

## Shaping

Instead of using step function (ie sparse reward) versus using a smooth reward, can use a smoother shaped reward

Shaped reward offers a smooth gradient for agent to follow → easier to learn

## Terminal Conditions

Bound exploration, stop time wasting if task can't be solved

Three kinds:
1. Time limits
2. Positive terminals
3. Negative terminals

## Positive vs Negative Rewards

**Positive rewards** encourage keeping on going:
- Agent approaches destination but never arrives because it keeps accumulating reward
- Can solve this by making the terminal state reward higher than any discounted expected reward for keeping on going

**Negative rewards** encourage reaching a terminal state as quickly as possible:
- If you don't want this, should avoid easier to reach terminal conditions when you give negative reward
- Using negative terminals → positive rewards, or at least reward that will end up positive on most episodes (given random exploration)

## Example: Guiding a Robotic Arm

Guiding a robotic arm using a normalized distance, raised to the power of 0.4 to give shape to the curve:
- Stays positive within our working area (can use negative terminals)
- Gradient is sharp towards the goal
- Never exceeds 1 - often best to bound reward between -1 and 1

`reward = 1 - (distance / distance_max) ^ 0.4`

## Example: Landing on the Moon

Break reward into two parts - in the air or touching surface

```python
# encourage fuel conservation
fuel_discount = fuel_remaining / total_fuel

if touching surface:
    if velocity < threshold:
        if position in landing_zone:
	    #  landed safely, give large reward
	    landing_reward = 100

	    reward = landing_reward * fuel_discount

	else:
	    reward = -10  # landed in wrong place
   else:
       reward = -100  # crashed
else:
    #  encourage good exploration
    distance_reward = 1 - (distance/distance_max)^0.4
    reward = distance_reward * fuel_discount
```

## Hidden State

If you reward for it, tell the agent about it. Tell the agent how far it is from goal if it gets rewarded

Don't reward for hidden states without a proxy

State needs to include information needed to solve the problem

## Pitfalls

Reward functions where there is a narrow path to success, surrounded by a sea of penalty

i.e. lunar lander:
- Can give agent info about how a slower approach trajectory
- Naive reward function has no gradient information about velocity
- Agent would have to explore a lot to figure out that slower is better here

Velocity will matter more as we get closer to the goal

```python
# naive
reward = 1 - distance^0.4

# reward for going slowly

dist_reward = 1 - distance^0.4
vel_discount = (1 - max(velocity, 0.1)) ^ (1 / max(distance, 0.1))

reward = dist_reward * vel_discount
```

Also possible to add them together and /2 - this would be a linear gradient.

The non-linear combination means that when close, agent receives reward for essentially only having a low velocity (this term dominates)

## Sequential or Conditional Tasks

Staged reward functions

Robot arm grasping

Make sure the reward is monotonically increasing (ie each transition gives more reward). Otherwise agent might learn to not complete the previous stage

```python
#  reward for lift after grasp
if fingers_closed:
    reward = pinch_rew + lift_rew * (object_height/target_height)^4

# first learn to grasp
else:
    reward = pinch_rew * (1 - (finger_dist / target_dist)^0.4)
```

If the reward function is becoming too complex, this is a sign that you should break the task down into concept networks

## Challenges and Strategies

Challenges and Strategies in Reinforcement Learning - Bonsai - [youtube](https://www.youtube.com/watch?v=w3fxPWYIpnQ)

Marcos Campos - head of AI

How to make reinforcement learning problems easier to solve

Dynamic programming = hardest of the main optimization problems (linear, quadratic, mixed-integer & dynamic)

### Key Challenges

- Not optimizing immediate action, but far ahead
- Temporal dimension
- Limited information about each action

### Reward Function Tradeoffs

- Sparse functions are easy to specify, hard to solve
- Non-sparse = hard to specify, easier to solve
- Combining different goals (ie safety and speed)
- Multi-objective problems:
  - No overall reward function combining multiple rewards/goals
  - Learn how to trade between goals based on env context

Tradeoff between sparse & non-sparse reward functions

### Scalability

i.e. sample inefficiency

Reinforcement learning is a sequential method

### Shaping Types

Agent should converge to the same solution for both shaped & non-shaped

Two types of shaping:
1. Reward function
2. Value function - bootstrap from a previously learned solution

Combining reward functions is an art - there is no theory (requires domain knowledge)

Potential functions = added to reward with a decaying factor (influence will disappear over time)

## Curriculum Learning

Breaks down learning process into lessons, ranging from easy to harder tasks

Later lessons mix material from earlier lessons with more advanced tasks

## Apprenticeship Learning

Use sample rollouts as guides for learning - imitation learning

Exploration occurs around the demonstrated performance

Pros:
- Constrains search space
- Faster convergence

Cons:
- Not every problem can be demonstrated
- Doesn't find innovative solutions

## Building Blocks

Combine blocks that can perform tasks or compute useful features

Allows reuse and specification of prior knowledge

i.e. combining forehand & backhand for tennis

Option framework = learning how to combine

Use previous skill or choose to learn new skills (continue to optimize the blocks)

### Concepts and Lessons

Concepts:
- Can be solved independently (ie minimize cost, control temperature)
- Useful behaviour in all or part of state space

Lessons:
- Different regimes of control (ie close or far from setpoint)
- Restriction on the state space to make learning easier

Make sure all the information needed to make a good decision is in the state

Lab notebook - watch what the policy is doing
