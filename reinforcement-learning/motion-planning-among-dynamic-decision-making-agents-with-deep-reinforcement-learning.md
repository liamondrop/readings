# Motion Planning Among Dynamic, Decision-Making Agents with Deep Reinforcement Learning

Collision avoidance among non-communicating, dynamic agents can be placed into two broad buckets:

1. Reaction-based methods, which use geometry/physics to infer the other agents' trajectories, and which are often necessarily short-sighted
2. Trajectory-based methods, which compute plans for the other agents, but which are typically computationally expensive and may require special knowledge of the agents unobserved state

The approach pioneered in [1] and [2] offloads the expensive operation of modeling complex interactions in an offline training step, allowing a real-world agent to quickly query the learned policy online.

The paper also discusses the benefits of using an abstracted "agent-level" representation of the world as input, as opposed to raw sensor input, as static objects and stationary agents may appear similar in, e.g. a raw laser scan, but will likely behave very differently if the ego robot gets too close.

The paper also discusses various approaches to modeling the environment in a way that is agent-aware, given that the observation inputs to a neural network generally need to be of a fixed size. Rather than using a fixed maximum number of agents, or else using raw sensor inputs (e.g. laser scan or camera image), or else maintaining an overhead map view, it proposes the use of an LSTM to handle a world with a variable and unbounded number of other objects/agents to consider. LSTMs are capable of encoding a sequence of information that is not time-dependent, and they leverage this property to model the world


[1] Decentralized, non-communicating multiagent collision avoidance with deep reinforcement learning
[2] Socially aware motion planning with deep reinforcement learning