[How is reinforcement learning better than conventional control techniques for robotics?](https://www.reddit.com/r/reinforcementlearning/comments/z1ttxb/how_is_reinforcement_learning_better_than/)

[Benjamin Recht: Optimization Perspectives on Learning to Control (ICML 2018 tutorial)](https://youtu.be/nF2-39a29Pw)

[The statistical foundations of learning to control - Benjamin Recht](https://youtu.be/gK1zHeLf8U0)

[A Mixed Integer Programming model predictive controller for a Flappy Bird Clone](https://github.com/philzook58/FlapPyBird-MPC)

[Machine Learning Control - textbook](http://faculty.washington.edu/sbrunton/mlcbook/)

[Data driven control](https://www.youtube.com/watch?v=oulLR06lj_E&list=PLMrJAkhIeNNQkv98vuPjO2X2qJO_UPeWR)

Historically control theory was mostly linear - get a linear set of equations then use some control method (Kalman filter is one) that uses linear inputs. But the world is non-linear.

## An Outsider's Tour of Reinforcement Learning - Ben Recht

[Part 2 - Total Control](http://www.argmin.net/2018/02/01/control-tour/)

**Control theory** = dynamical systems with inputs, internal state and outputs. If we turn off the input, the state is all we need to predict future output. Optimal control = the set of inputs that minimizes some objective (usually expected reward):

$$x_{t+1} = f(x_t, u_t, e_t)$$

$f$ = state transition rule → use optimization. $f$ as an MDP = discrete values of $x$ with probability tables.

[Linearization principle](http://www.argmin.net/2018/02/05/linearization):

> If a machine learning algorithm does crazy things when restricted to linear models, it's going to do crazy things on complex nonlinear models too

(Yet deep nets can memorize random labels and still generalize.)

[Linear Quadratic Regulator (LQR)](http://www.argmin.net/2018/02/08/lqr/) = a baseline for RL.

**Analytics taxonomy**: descriptive (summarizing), predictive, prescriptive (guides actions to guarantee outcomes).
