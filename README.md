# MA-DRL-Udacity

<img src="https://user-images.githubusercontent.com/10624937/42135623-e770e354-7d12-11e8-998d-29fc74429ca2.gif">


# DRL - MADDPG Algorithm - Tennis Collaboration Continuous Control
Udacity Deep Reinforcement Learning Nanodegree Program - Tennis Collaboration Continuous Control


### Observations:
- To run the project just execute the <b>main.py</b> file.
- There is also an .ipynb file for jupyter notebook execution.
- If you are not using a windows environment, you will need to download the corresponding <b>"Tennis"</b> version for you OS system. Mail me if you need more details about the environment <b>.exe</b> file.
- The <b>checkpoint.pth</b> has the expected average score already hit.


### Requeriments:
- tensorflow: 1.7.1
- Pillow: 4.2.1
- matplotlib
- numpy: 1.11.0
- pytest: 3.2.2
- docopt
- pyyaml
- protobuf: 3.5.2
- grpcio: 1.11.0
- torch: 0.4.1
- pandas
- scipy
- ipykernel
- jupyter: 5.6.0


## The problem:
- The task solved here refers to a collaboration continuous control problem where two agents must be able to play "tennis"
in collaboration, that is, the longer the rally goes the higher will be the reward that both agents will earn.
- It's a continuous problem because the action has a continuous value and the agents must be able to provide this value instead of just chose the one with the biggest value (like in discrete tasks where it should just say which action it wants to execute).
- In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.
- The task is episodic, and in order to solve the environment, the agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents).


## The solution:
- For this problem, the DDPG code provided by Udacity was used as a reference.
- The main hurdle was sharing the experiences between the agents.
- I've noticed that the convergence is still a little bit unstable and for the future, I plan to make an improvement upon the neural network structure and check if I can have a faster convergence for this task.


To run the code follow the below instructions :

Run tennis_MA.ipynb file to train the agent.

Actor Critic model and the agen code are inside the tennis_MA.ipynb file itself.
