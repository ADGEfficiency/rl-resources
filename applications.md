[Reinforcement Learning Applications](https://medium.com/@yuxili/rl-applications-73ef685c07eb)

[A Curated List of Reinforcement Learning Applications](https://rl-book.com/applications/)

## Energy

[Reinforcement Learning for Demand Response](https://forum.climatechange.ai/t/reinforcement-learning-for-demand-response/237)

## OpenAI Retro Contest

[OpenAI Retro Contest Report (#15 score, #2 write-up)](https://medium.com/@olegmrk/openai-retro-contest-report-b870bfd014e0)

[Retro Contest: Results - blog post](https://blog.openai.com/first-retro-contest-retrospective/)

Top results all came from extending existing algorithms - PPO, Rainbow. Top performance = 4692 (max 10000), so the Sonic benchmark is a good one. Uses wall-clock time. Surprising that top submissions were often tuned existing implementations (importance of hyperparameters).

**Dharmaraja (winners)**: PPO, RGB images, augmented action space (more button combinations), augmented reward function (bonus for visiting new states, judged by hash of screen). Also tried DeepMimic, YOLO object detection + Sonic-specific ideas (none worked out).

**Mistake**: Rainbow - optimized n, extra CNN layer (slower but better training), lower DQN target update interval. [source on github](https://github.com/xupe/mistake-in-retro-contest-of-OpenAI)
