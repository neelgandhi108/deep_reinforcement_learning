Project 1: Reinforcement Learning for Navigation
Author: Neel Gandhi

Introduction
This project delves into the fascinating realm of Reinforcement Learning (RL) through the prism of value-based methods, particularly the formidable Deep Q-learning and its advanced iterations. The mission is to harness the prowess of these algorithms to facilitate an agent in mastering an intricate Unity environment. This environment, comprising a sprawling, 37-dimensional state space, tasks the agent with skillfully maneuvering to gather rewarding yellow bananas (+1), while meticulously avoiding detrimental blue bananas (-1). With a repertoire of four actions – moving left, moving right, moving forward, and moving backward – the agent's journey unfolds in a complex yet captivating landscape.

Random Agent

Problem Exploration
The crux of this project revolves around applying value-based reinforcement learning techniques to navigate and optimize the banana collection process. The task at hand involves training an agent to make informed decisions, maximizing its cumulative rewards by strategically selecting actions within the environment. The environment's state space encompasses 37 dimensions, encapsulating vital information such as the agent's velocity and ray-based perceptions of objects in its forward direction. The agent can execute a range of actions, corresponding to the four discrete choices available.

Technical Implementation
At the heart of the technical endeavor lies the profound Deep Q-learning, an off-policy RL algorithm renowned for outshining human-level performance in the realm of Atari games. This algorithm evolves from the Q-learning approach, aiming to learn the action-value function, denoted as Q(s, a), where s signifies the current state and a represents the action in consideration.

However, in the realm of continuous state spaces, a tabular representation is infeasible. Enter the concept of a Function Approximator, which employs a parameter θ to approximate the action-value function, denoted as $\hat{Q} (s, a; \theta)$. This approximation transforms the learning process into a supervised learning problem, wherein $\hat{Q}$ simulates the expected value and $R + \gamma * \max (Q(s', a))$ serves as the target. The incorporation of a neural network, a quintessential element of Deep Learning, serves as the function approximator. Specifically, a 2-hidden layer network, each layer housing 64 hidden units with relu activation, is adopted. The Adam optimizer takes charge of adjusting the optimal weights.

However, the algorithm in its raw form exhibits instability. To counteract this, two pivotal techniques are harnessed:

Fixed Q-targets: This involves segregating the Q-target calculation from the parameter updates. The incorporation of two distinct networks, the online network and the target network, helps mitigate the issue. The target network's parameters are periodically updated based on the online network, ensuring target stability.
Experience Replay: To enhance stability, a Replay Buffer is employed to store experiences. By randomly sampling experiences from this buffer, the temporal sequence is broken, promoting independent sample learning.
Advanced Techniques Implemented
The endeavor extends beyond the confines of the conventional DQN algorithm. Two advanced techniques are harnessed to augment learning:

Double DQN: Aimed at mitigating value overestimation, this technique entails disentangling Q-target calculations. The online network selects the best action, while the target network evaluates the selected action. This bifurcation serves as a check against overestimation errors, enhancing decision-making robustness.
Dueling Network: This technique transcends the single output stream of conventional DQNs, introducing a shared feature extractor layer. The streams, one evaluating the state's value function (V(s)) and the other the advantage function for each action (A(a, s)), harmonize to yield an aggregated Q-value. This nuanced approach better guides action selection.
Hyperparameters and Training
The experiment incorporates diverse hyperparameters:

Replay buffer size: 1e5
Batch size: 64
Discount factor ($\gamma$): 0.99
Soft update coefficient ($\tau$): 1e-3
Learning rate: 5e-4
Update interval: 4
Number of episodes: 500
Max timesteps per episode: 2000
Epsilon start: 1.0
Epsilon minimum: 0.1
Epsilon decay: 0.995
Results and Insights
The culmination of this ambitious endeavor is manifest in the results achieved. The trained agent adeptly navigates the intricate landscape, skillfully avoiding obstacles while acquiring yellow bananas:

Trained Agent

The pinnacle of achievement is realized through the Double DQN, boasting an impressive feat of achieving the coveted reward of +13 in just 377 episodes. Notably, the Dueling Double DQN, despite its potential, did not seize the top spot, potentially due to hyperparameters. The comparative performance is eloquently depicted through reward plots:

Double DQN	DQN	Dueling DQN
Double DQN	DQN	Dueling Double DQN
Future Prospects and Beyond
While this project is indeed a resounding success, there's always room for refinement and innovation:

Prioritized Replay: Harnessing the benefits of prioritized replay (paper) holds potential to elevate performance.
Exploring DQN Variants: Venturing into other DQN variants like multi-step bootstrap targets, Distributional DQN, and Noisy DQN promises potential enhancements.
Hyperparameter Exploration: Iterating through hyperparameters for Double DQNs and Dueling Double DQNs could unveil more robust solutions.
Conclusion
In conclusion, the journey embarked upon in this project delves into the intricate realm of Reinforcement Learning, unraveling the potential of advanced value-based techniques. The accomplishments achieved through Double DQNs and Dueling Double DQNs underscore the potency of RL algorithms in navigating complex environments. With the roadmap for future enhancements laid out, the realm of possibilities is boundless.