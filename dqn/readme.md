[Curt-Park/rainbow-is-all-you-need](https://github.com/Curt-Park/rainbow-is-all-you-need)

## Dopamine and Reward Prediction

<!-- From Schultz Neural Substrate (see 1997_Schultz_neural_substrate_reward.pdf) -->

**Dopamine** - connection between TD error and dopamine in the brain. Dopamine signal can be modelled as a TD error. Phasic activity of dopamine is triggered by a reward. With continued trials, the dopamine signal moves back towards the time of the prediction (same as the TD error does - a backup).

Dopamine neurons of the ventral tegmental area (VTA) and substantia nigra are identified with processing of rewarding stimuli. Send axons to parts of the brain involved in motivation and goal directed behaviour (striatum, nucleus accumbens and frontal cortex).

After repeated pairings of visual + auditory cues → reward, **neurons change activation time from just after reward to the time of cue onset**. If reward is not delivered, neurons depress below their basal firing rate at exactly when the reward should have occurred.

> Dopamine neurons do not simply report the occurrence of appetitive events. Rather, their outputs appear to code for a deviation or error between actual reward received and predictions of the time and magnitude of the reward.

**Blocking**: no further learning takes place when the reward is entirely predicted by a sensory cue. If a light consistently predicts food, then a light+sound pair predicts food, the rat learns the light continues to predict food but the sound predicts nothing - the sound adds no new predictive information. Learning is driven by deviations or "errors" between predicted and actual reward.

Output of dopamine neurons is consistent with a scalar signal. Dopamine rewards don't distinguish between the type of rewarding stimuli (issue: animal may learn to approach food when it is actually thirsty). Dopamine delivery has dramatic influence on working memory - modulates cognition. Prediction errors are delivered to widespread targets. Concept of **attention** - evidence that attention occurs at the level of dopamine neurons.

Engineered systems face the same challenges, but the rewards/punishments are determined by design goals.
