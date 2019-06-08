# Learning Robust Rewards with Adversarial Inverse Reinforcement Learning

Adversarial Inverse RL (AIRL) builds on the GAN-like framework proposed by Guided Cost Learning (GCL - Finn et al 2016), with the discriminator corresponding to an odds ratio between the policy and the reward distribution. It also seeks to overcome the rewards ambiguity problem within the standard IRL framework.

In our experiments, they aim to answer two questions:
1. Can AIRL learn disentangled rewards that are robust to changes in environment dynamics?
2. Is AIRL efficient and scalable to high-dimensional continuous control tasks?

To answer 1, they evaluate AIRL in transfer learning scenarios, where a reward is learned in a training environment, and optimized in a test environment with significantly different dynamics.

To answer 2, they compare AIRL as an imitation learning algorithm against GAIL (Ho & Ermon, 2016) and GCL on standard benchmark tasks. AIRL performs on par with GAIL in a traditional imitation learning setup while vastly outperforming it in transfer learning setups, and outperforms GCL in both settings. It is worth noting that, AIRL is the only IRL algorithm that scales to high dimensional tasks with unknown dynamics, and although GAIL (Ho & Ermon, 2016) resembles an IRL algorithm in structure, it does not recover disentangled reward functions, making it unable to re-optimize the learned reward under changes in the environment, as we illustrate below.