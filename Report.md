## DDPG Reinforcement algorithm for Unity ML-Agents Tennis Environment


Details of environment :
```
Number of agents: 2
Size of each action: 2
There are 2 agents. Each observes a state with length: 24
```
In this environment, two agents control rackets to bounce a ball over a net.

### State Space :

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation.

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
Input layer - 24*2 neurons
Hidden layer - 256 neurons
Hidden layer - 128 neurons
Output layer - 2 neurons
```

### Critic Network :
It is similar to actor network but has additions of action neurons in first hidden layer and has only 1 neuron in the output layer. 

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

1. We have class of Ring buffer with deque of tuple [State , Actions , Reward , Next state , Done ]
2. We are using Relu after every fully connveted layer.
3. We are adding actions in the critic network with the second hidden layer.
4. Two networks for each agent are maintained for each Actor and Critic in order to have a smooth learnings. So we track a total of 4 networks.
5. We add actions of both the agent to the layer of critic for each individual agents.

### DDPG algorithm.
```
number of episodes=1000, 
```

## Final Results :

### Results for number of episodes.

![Graph_Episode_score](https://user-images.githubusercontent.com/40532456/124676300-e476b900-de83-11eb-81e4-a195ca248dfd.png)

![Training_Episode_reward](https://user-images.githubusercontent.com/40532456/124676310-e8a2d680-de83-11eb-899e-6576c4a6e7d7.png)


**Hence the game can be solved with +0.5 score on an average of 100 episodes in 520 episodes. Giving a score of 0.511**

### Ideas to improve on the results.

1. Various other algotihms like TRPO, PILCO, PPO, A3C and D4PG can be tested.
2. PPO can be tried and compared with A2C.
3. Single actor critic netowork to train both the agents.
