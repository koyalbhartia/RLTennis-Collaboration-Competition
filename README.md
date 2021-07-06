# RLTennis-Collaboration-Competition
Two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play and gain 0.5 points over 100 episodes.

### Glimpse of training of collabrative multi-agent system.

https://user-images.githubusercontent.com/40532456/124676587-6ff04a00-de84-11eb-896d-b435a0746165.mp4

If you want to train your own model you will refer the file.

[Training program](https://github.com/koyalbhartia/RLTennis-Collaboration-Competition/blob/main/Collab_Compete/Tennis.ipynb)

The trained models can be found here:
[Agent_0_Actor model](https://github.com/koyalbhartia/RLTennis-Collaboration-Competition/blob/main/Collab_Compete/agent0_checkpoint_actor.pth)
[Agent_1_Actor model](https://github.com/koyalbhartia/RLTennis-Collaboration-Competition/blob/main/Collab_Compete/agent1_checkpoint_actor.pth)

[Agent_0_Critic model](https://github.com/koyalbhartia/RLTennis-Collaboration-Competition/blob/main/Collab_Compete/agent0_checkpoint_critic.pth)
[Agent_1_Critic model](https://github.com/koyalbhartia/RLTennis-Collaboration-Competition/blob/main/Collab_Compete/agent1_checkpoint_critic.pth)

## Details of environment :
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

### Solving criterias

The task is episodic, and in order to solve the environment, your agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,

After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
This yields a single score for each episode.
The environment is considered solved, when the average (over 100 episodes) of those scores is at least +0.5.

## Setup environment:

1. First we have to install conda once the conda is installed we need to update the bash script.  [Install anaconda](https://docs.anaconda.com/anaconda/install/linux/).
Other tools used in the project are Python 3.6, PyTorch, NumPy, UnityEnvironment package and Matplotlib


2. Run the following commands in the terminal.
```
conda create --name drlnd python=3.6
source activate drlnd
```

3. Clone this repo :
```
git clone https://github.com/koyalbhartia/RLTennis-Collaboration-Competition
```

4. Install python dependencies:
```
cd DDPG-Continuous-Control/python
pip install .
```

5. Setup drlnd environment :
```
python -m ipykernel install --user --name drlnd --display-name "drlnd"
```
6. Open Jupyter notebook to start learning and experimenting :

```
cd RLTennis-Collaboration-Competition/Collab-Compete
jupyter notebook
```

**Note : Do not forget to select Kernal >> Change kernal >> drlnd**

7. Edit the location of the Reacher linux in code cell 2 with your username and run the notebook( Hit  **Shift + Enter**) 


## Results :

### Our Average score vs Episodes.

![Graph_Episode_score](https://user-images.githubusercontent.com/40532456/124676015-57cbfb00-de83-11eb-8b85-39a3d1696082.png)

