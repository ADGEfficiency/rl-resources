---
id: 2019-botvinick-rl-fast-slow
aliases: []
tags:
  - reinforcement-learning
  - machine-learning
---
Two techniques are singled out: episodic deep RL and meta-RL.

Slowness in early deep RL has two distinct sources:
- Source 1 — incremental parameter adjustment: gradient descent must take small steps to generalise well and to avoid catastrophic interference (overwriting earlier learning). Small steps = slow.
- Source 2 — weak inductive bias: generic neural nets have huge parameter counts and can fit almost anything (high variance), which by the bias–variance trade-off means they need lots of data.
- Intricacy: these two are treated as separable problems with separable fixes, and the paper's structure mirrors this — episodic RL attacks source 1, meta-RL attacks source 2. The payoff at the end is the claim that both fixes secretly rely on slow learning.

The bias–variance trade-off is the theoretical spine of the whole argument
- Stronger initial assumptions (narrow hypothesis set) → less data needed, but only if the correct hypothesis is inside that set.
- Weaker bias → can learn a wider range of patterns but is less sample-efficient.
- Argument against strong bias: a narrow hypothesis set that excludes the truth will fail or mislead. So bias is a double-edged sword, which sets up the next problem: how does a learner know which biases to adopt?
- Link: this is essentially the machine-learning restatement of the classic "no free lunch" idea, and connects to hierarchical Bayesian models where priors carry the inductive bias (the authors flag this near the end via Griffiths/Tenenbaum).

Episodic deep RL avoids slow incremental updating by storing and reusing past events
- Instead of nudging weights slowly, keep an explicit record of past situations and reuse it directly when deciding.
- Mechanism: represent the current state, compare it to stored states, and pick the action tied to the most valuable similar past outcomes (a weighted sum of stored discounted rewards, weighted by state similarity).
- It parallels non-parametric ML and instance-/exemplar-based theories in psychology (Logan; Smith & Medin).
- Advantage: each experience can be used immediately, so learning is fast.
- The twist (argument against reading it as "pure" fast learning): the similarity judgments depend on good internal representations, and those embeddings are still learned slowly by gradient descent. So fast episodic learning sits on top of slow representation learning.
- Commentary: this is the paper's rhetorical move in miniature — it never claims to eliminate slow learning, only to relocate it. That is intellectually honest but also means "fast RL" is a somewhat loaded label.

Meta-RL speeds learning by learning the inductive biases themselves ("learning to learn")
- If strong biases speed learning but must be correct, get them from past experience across related tasks — this is meta-learning, called "learning to learn" in psychology.
- Harlow (1949) is the anchoring precedent: monkeys given repeated 6-trial object-discrimination problems eventually solved each new pair in one shot, inferring the abstract rule ("one object is always rewarded regardless of position").
- Implementation (Wang 2016; Duan 2016): train a recurrent net over many related RL tasks with very slow weight updates; the weights absorb what is common across tasks but cannot solve any single task on their own.
- Remarkable result: the recurrent network's activity dynamics come to implement their own RL algorithm that solves each new task quickly — "one RL algorithm gives birth to another."
- Again the fast/slow dependency: the fast inner algorithm exists only because slow outer weight-learning endowed it with useful biases.

Evolution can be folded in as the slowest learning loop, dissolving the learned/innate distinction
- In biology, hand-wired architectural biases can be reframed as products of a slower learning process: evolution.
- Implication: evolution does not produce a general-purpose learner but one exploiting regularities of the environments brains evolved in.
- This yields a cascade of timescales from millennia (evolution) to milliseconds (activity dynamics), each slower level supplying biases to the next faster one.
- Link: AI work on evolving architectures, reward functions, and learning rules (NEAT, Baldwin effect, Hinton & Nowlan) is offered as a laboratory for this.
- Commentary: elegant, and genuinely reframes the nature/nurture axis as a continuum of learning rates — but it also makes the framework so encompassing that it risks explaining everything and predicting little.

[Reinforcement Learning, Fast and Slow - Reinforcement_Learning_Fast_and_Slow.pdf](file:///Users/adamgreen/Downloads/Reinforcement_Learning_Fast_and_Slow.pdf)

Deep RL has produced superhuman AI but its relevance to human learning is contested
- Deep RL marries neural networks with reward/punishment learning, and since ~2014 has beaten humans at Atari, Go, chess, no-limit poker, and multiplayer games.
- Its learning mechanisms were inspired by animal conditioning and are thought to relate to dopamine-based reward learning, so it looks like a natural bridge to psychology/neuroscience.
- The catch is sample efficiency: early deep RL needed orders of magnitude more experience than human experts to reach the same level, so critics (Lake et al. 2015; Marcus 2018) argued it is too slow to model human learning.
- Commentary: the paper is explicitly a rebuttal to those two named critiques. Worth keeping that framing in mind — it is a persuasive piece by DeepMind authors defending their own research programme, not a neutral survey.

The critique only applies to the first wave of deep RL, and newer methods are much faster
- The authors concede the slowness charge is fair for ~2013-era methods (Mnih et al. DQN).
- They claim subsequent innovations dramatically raise sample efficiency, reviving deep RL as a candidate model of human learning.
- Two techniques are singled out: episodic deep RL and meta-RL.

Slowness in early deep RL has two distinct sources
- Source 1 — incremental parameter adjustment: gradient descent must take small steps to generalise well and to avoid catastrophic interference (overwriting earlier learning). Small steps = slow.
- Source 2 — weak inductive bias: generic neural nets have huge parameter counts and can fit almost anything (high variance), which by the bias–variance trade-off means they need lots of data.
- Intricacy: these two are treated as separable problems with separable fixes, and the paper's structure mirrors this — episodic RL attacks source 1, meta-RL attacks source 2. The payoff at the end is the claim that both fixes secretly rely on slow learning.

The bias–variance trade-off is the theoretical spine of the whole argument
- Stronger initial assumptions (narrow hypothesis set) → less data needed, but only if the correct hypothesis is inside that set.
- Weaker bias → can learn a wider range of patterns but is less sample-efficient.
- Argument against strong bias: a narrow hypothesis set that excludes the truth will fail or mislead. So bias is a double-edged sword, which sets up the next problem: how does a learner know which biases to adopt?
- Link: this is essentially the machine-learning restatement of the classic "no free lunch" idea, and connects to hierarchical Bayesian models where priors carry the inductive bias (the authors flag this near the end via Griffiths/Tenenbaum).

Episodic deep RL avoids slow incremental updating by storing and reusing past events
- Instead of nudging weights slowly, keep an explicit record of past situations and reuse it directly when deciding.
- Mechanism: represent the current state, compare it to stored states, and pick the action tied to the most valuable similar past outcomes (a weighted sum of stored discounted rewards, weighted by state similarity).
- It parallels non-parametric ML and instance-/exemplar-based theories in psychology (Logan; Smith & Medin).
- Advantage: each experience can be used immediately, so learning is fast.
- The twist (argument against reading it as "pure" fast learning): the similarity judgments depend on good internal representations, and those embeddings are still learned slowly by gradient descent. So fast episodic learning sits on top of slow representation learning.
- Commentary: this is the paper's rhetorical move in miniature — it never claims to eliminate slow learning, only to relocate it. That is intellectually honest but also means "fast RL" is a somewhat loaded label.

Meta-RL speeds learning by learning the inductive biases themselves ("learning to learn")
- If strong biases speed learning but must be correct, get them from past experience across related tasks — this is meta-learning, called "learning to learn" in psychology.
- Harlow (1949) is the anchoring precedent: monkeys given repeated 6-trial object-discrimination problems eventually solved each new pair in one shot, inferring the abstract rule ("one object is always rewarded regardless of position").
- Implementation (Wang 2016; Duan 2016): train a recurrent net over many related RL tasks with very slow weight updates; the weights absorb what is common across tasks but cannot solve any single task on their own.
- Remarkable result: the recurrent network's activity dynamics come to implement their own RL algorithm that solves each new task quickly — "one RL algorithm gives birth to another."
- Again the fast/slow dependency: the fast inner algorithm exists only because slow outer weight-learning endowed it with useful biases.

The two-loop framing makes the fast/slow relationship concrete
- Outer loop: slow, standard deep RL tuning of connection weights across many tasks.
- Inner loop: a fast learning algorithm that emerges in the recurrent activity dynamics.
- Bandit illustration: after training, with weights frozen, the network explores a new two-armed bandit and homes in on the better arm, competitive with hand-crafted algorithms (UCB, Thompson sampling, Gittins).
- Sharpest claim: the inner algorithm can outperform the outer one that created it, because it carries task-matched inductive biases (correlated-bandit training → faster convergence than independent-bandit training).
- Intricacy worth flagging: the inner loop is model-based in behaviour even though the outer training procedure is model-free — the paper leans on this in Box 4 as an explanation for why brain dopamine signals carry model-based information.

Episodic meta-RL combines both techniques since they are not mutually exclusive
- Meta-RL runs inside a recurrent net; an episodic memory is layered on top to reinstate past hidden-activity patterns rather than value estimates.
- On re-encountering a task, the system reinstates the previous hidden state, letting prior learning immediately shape current policy — recognising a task and retrieving its stored solution.
- Ritter et al. (2018): first encounter benefits from meta-RL's rapid adaptation; later encounters benefit from one-shot episodic retrieval, avoiding re-exploration.
- Commentary: this is the neatest part of the argument because the two "fixes" compose cleanly, but it is also the thinnest on independent evidence — mostly simulation in bandit/navigation toy tasks.

The techniques undercut the sample-inefficiency objection to deep RL as a brain model
- If deep RL need not be slow, the main reason for dismissing it as a model of human/animal learning weakens.
- Beyond defence, each technique suggests specific new hypotheses rather than just a rebuttal.

Episodic deep RL connects to instance-based memory and hints at how representation learning shapes value
- It offers an account of how instance-based processing could support reward-driven learning.
- It fits accumulating evidence that human/animal value estimates draw on retrieved memories of specific past action–outcome events (Gershman & Daw; Bornstein).
- It highlights an under-explored question: how fast episodic RL depends on slower representation/metric learning — well studied for memory per se, much less for reward-based learning.

Meta-RL maps onto prefrontal cortex tuned by dopamine
- Wang et al. (2018) propose: slow dopamine-driven synaptic change tunes prefrontal recurrent dynamics so PFC implements its own fast learning algorithm (inner loop = PFC dynamics, outer loop = dopamine plasticity).
- Supporting evidence: dlPFC neurons (Tsutsui et al.) code last action, last reward, and their interaction — exactly the variables a learning policy needs; trained meta-RL units acquire strikingly similar coding.
- It offers a single explanation for a puzzle: dopamine RPEs carry model-based information (Daw et al.) even though model-free training should not produce that — meta-RL reproduces model-based RPEs from model-free training.
- Commentary: this is the most falsifiable neuroscience claim in the paper and also the most load-bearing; the "similar coding properties" argument rests on qualitative resemblance, which is suggestive rather than decisive.

Episodic meta-RL was inspired by, and feeds back into, neuroscience of reinstatement
- The reinstatement mechanism was drawn from evidence that episodic-memory circuits reinstate cortical activity patterns, including in working-memory areas.
- It gives a parsimonious account of reported interactions between episodic and model-based control in humans, and illustrates meta-learning operating over multiple memory systems.

The organising thesis: fast learning always relies on slow learning
- In meta-RL, slow weight learning establishes the inductive biases guiding fast adaptation.
- In episodic RL, slow learning shapes state representations, which encode biases about which states count as similar.
- Episodic RL also has a built-in architectural bias — a smoothness assumption that similar states call for similar actions — wired in rather than learned.
- Distinction drawn: "learned bias" (meta-RL) vs "architectural/algorithmic bias" (episodic RL, convolutional nets' translation invariance).
- Commentary: "fast learning relies on slow learning" is doing a lot of work as a unifying slogan. It is close to unfalsifiable as stated — almost any fast system can be described as resting on some slower substrate — so its value is as an organising lens rather than a testable claim.

Evolution can be folded in as the slowest learning loop, dissolving the learned/innate distinction
- In biology, hand-wired architectural biases can be reframed as products of a slower learning process: evolution.
- Implication: evolution does not produce a general-purpose learner but one exploiting regularities of the environments brains evolved in.
- This yields a cascade of timescales from millennia (evolution) to milliseconds (activity dynamics), each slower level supplying biases to the next faster one.
- Link: AI work on evolving architectures, reward functions, and learning rules (NEAT, Baldwin effect, Hinton & Nowlan) is offered as a laboratory for this.
- Commentary: elegant, and genuinely reframes the nature/nurture axis as a continuum of learning rates — but it also makes the framework so encompassing that it risks explaining everything and predicting little.

The perspective is acknowledged as not wholly new
- Learning-to-learn has been in psychology for decades (Harlow); hierarchical Bayesian models already cast priors as inductive biases; evolutionary biology has touched related ideas.
- The claimed novelty is the mechanistic neural-network/RL instantiation, not the underlying concept.
- Commentary: this candour is welcome and slightly undercuts the paper's own framing — much of the "insight" is a re-description of Bayesian priors and complementary-learning-systems theory (Kumaran/McClelland) in RL vocabulary.

Open problems the authors flag
- Can sample-efficient deep RL scale to the rich abstractions underlying human intelligence, and what training environments would that require?
- Does human efficiency use mechanisms like these, and does anything like gradient descent actually occur in the brain, or a different mechanism?
- Which inductive biases matter most for human environments, and how much is evolved/innate vs learned?
- How to capture that humans are active, strategic information-seekers — i.e. exploration is directed, not the passive/random exploration in most of the models discussed.
- Commentary: the last point is the most telling gap — nearly every technique reviewed treats exploration as given or random, yet directed exploration is arguably central to why humans are sample-efficient in the first place.
