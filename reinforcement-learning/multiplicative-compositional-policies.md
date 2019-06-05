# Learning Composable Hierarchical Control with Multiplicative Compositional Policies

For autonomous agents to perform sophisticated tasks, they need to be able to repurpose and recombine previously learned skills. Essentially, they need to learn how to walk and chew gum simultaneously. 

[This video](https://www.youtube.com/watch?v=ChxSx8-sX_c) gives a nice summary.

A complex behavior can be viewed as a combination of primitive skills. The standard hierarchical formulation for this is to use a gating function, which acts as a series of weights, giving the likelihood of activating each of the primitive skills for a given task as a linear combination. This approach is limited in that only one primitive can be activated at a time, restricting the range of behaviors that can be produced by the policy. What this means in practice is that more complex tasks, such as a humanoid that can both walk and carry a load to a particular destination, tend to fail in the standard hierarchical/mixture of experts approach. This paper proposes to use a multiplicative composition scheme, which makes it possible to activate multiple primitives at once. The gating function's weights determine how much each primitive influences the composite behavior.

The basic idea:
* Given a state, each primitive outputs an action distribution as a Gaussian.
* The gating function uses both the state and a task specific goal to determine the weights to each primitive.
* Applying these weights creates an interpolated composite action distribution.

One challenge is determining which primitive tasks should be trained. The paper proposes using something like imitation learning to train the primitive tasks, but approaches such as the one proposed in [Diversity is All You Need](https://github.com/liamondrop/readings/blob/master/reinforcement-learning/diversity-is-all-you-need.md), provide a possibly more interesting way to create a maximally diverse set of primitive skills that can be recombined to achieve robust and general complex behaviors. That said, imitation-learned tasks tend to provide more "natural" behavior than those often learned by policies learned from scratch and there is some value to being able to compose these, as long as the imitation-learned policies are flexible enough. The demonstrations shown in the video certainly look promising.
