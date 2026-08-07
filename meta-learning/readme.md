# Meta-Learning and Reinforcement Learning

<!-- See 2019_Botvinick_fast_slow.pdf -->

Deep RL inspired by animal conditioning.

## Two Sources of Slowness in Deep RL

**Requirement of incremental parameter adjustment**:
- Adjustment must be small to maximize generalization & avoid forgetting

**Weak inductive bias**:
- Any learning faces the bias-variance tradeoff - the stronger the initial inductive bias, the less data needed to learn (if the initial bias matches the data)
- Weak inductive bias → master a wider range of patterns (higher variance)
- Strong inductive bias → faster learning

## Two Techniques to Mitigate Sample Efficiency

**Episodic RL**:
- Combats parameter adjustment
- Keep a record of past events; compare new situation to stored representations of past events
- Embeddings are learnt slowly - dependence of fast learning on slow
- Similarity weightings

**Meta RL**:
- Combats the weak inductive bias
- Recurrent neural net trained on interrelated tasks - again a connection between slow & fast

Can combine episodic & meta. Slow learning establishes inductive biases to be used in fast learning. Conv nets build in the inductive bias of translation invariance; the memory store is itself a form of inductive bias.

## Learning to Learn

<!-- From Levine lecture -->

Using past data to learn new tasks quicker (rather than just to generalize). Use a policy that is optimized for a fast update from gradients. Visual meta imitation learning.
