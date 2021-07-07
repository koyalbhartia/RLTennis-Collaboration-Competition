## DDPG Reinforcement algorithm for Unity ML-Agents Tennis Environment


Details of environment :
```
Number of agents: 2
Size of each action: 2
There are 2 agents. Each observes a state with length: 24
```
In this environment, two agents control rackets to bounce a ball over a net.

### State Space :

The state size is 24. The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation.

### Action Space :

Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.

### Reward :

If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.

## Solving criterias of the problem. 

The task is episodic, and in order to solve the environment, your agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,

After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
This yields a single score for each episode.
The environment is considered solved, when the average (over 100 episodes) of those scores is at least +0.5.


## Neural Network details :
### Actor Network :
```
Input layer - 24*2 = 48 neurons
Hidden layer - 256 neurons
Hidden layer - 128 neurons
Output layer - 2 neurons
```

### Critic Network :

```
Input layer - 24*2 = 48 neurons
Hidden layer - 256 + (2*2) = 260 neurons
Hidden layer - 128 neurons
Output layer - 1 neuron
```

### Agent parameters :
```
BATCH_SIZE = 128        # minibatch size
BUFFER_SIZE = int(1e6)  # replay buffer size
GAMMA = 0.99            # discount factor
LR_ACTOR = 1e-3         # learning rate of the actor 
LR_CRITIC = 1e-3        # learning rate of the critic
TAU = 6e-2              # for soft update of target parameters
WEIGHT_DECAY = 0        # L2 weight decay
UPDATE_EVERY = 1        # time steps between network updates
N_UPDATES = 1           # number of times training
ADD_NOISE = True
eps_start = 6           # Noise level start
eps_end = 0             # Noise level end
eps_decay = 500         # Number of episodes to decay over from start to end

```

### DDPG parameters.
```
number of episodes=3000, 
```
### Implementation

1. Two networks are maintained for each Actor and Critic in order to have a smooth learnings.
2. Actor-Critic model is employed in which the Critic model learns the value function and uses it to determine how the Actor’s policy based model should change.
3. The Actor brings the advantage of learning in continuous actions space without the need for extra layer of optimization procedures required in a value based function while the Critic supplies the Actor with knowledge of the performance.
4. The learning rate for both Actor and Critic is 1e-3 with soft update of target set to the same 6e-2.
5. A Replay buffer maintains the tuple [State , Action , Reward , Next state , Done ]
6. Relu is used after every fully connveted layer.
7. Actions of both the agents are added to the layer of critic for each individual agents.
8. Two networks for each agent are maintained for each Actor and Critic in order to have a smooth learnings. So we actually track a total of 4 networks.


## Final Results :

### Results for number of episodes.

![Graph_Episode_score](https://user-images.githubusercontent.com/40532456/124676300-e476b900-de83-11eb-81e4-a195ca248dfd.png)

Training and rewards as seen after 400 episodes:

![Training_Episode_reward](https://user-images.githubusercontent.com/40532456/124676310-e8a2d680-de83-11eb-899e-6576c4a6e7d7.png)

The environment is considered solved when average reward (over 100 episodes) of at least +0.5 is achieved.

**Hence the game can be solved with +0.5 score on an average of 100 episodes in 528 episodes. Giving a score of 0.511**

### Ideas to improve on the results.

1. Various other algotihms like TRPO, PILCO, PPO, A3C and D4PG can be tested.
2. PPO can be tried and compared with A2C.
3. Single actor critic netowork to train both the agents.
4. Algorithms like Distributed Distributional Deterministic Policy Gradients can be used to compare performance.
