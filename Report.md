# DRL - Multi-Agent DDPG Algorithm - Tennis Collaboration

### Model Architecture
The  DDPG code in PyTorch was used from module 3 to employ two agents acting independently, but with a shared experience buffer. 
Each agent has its own set of deep neural networks (local and target actors and critics), each with two hidden layers of 256-128 nodes, with ReLU activation functions on the hidden layers and tanh on the output layers. 
The agents shared one experience memory buffer.

### Hyperparameters
A learning rate of 1e-3 on each DNN and batch size of 128 were used along with replay buffer size of 1e6, gamma .99 and Tau of 6e-2. Each agent took one step, then learned once, then repeated. After optimizing these hyperparameters, the agents were learning and achieving the desired goal of a 0.5 average reward. However, the agents took several hundred episodes to gain traction and start playing effectively. I determined that the exploitation-exploration balance needed further work to have the agents learn faster.

### Exploratory Boost

To address this balance, I created the Exploratory Boost method. The approach essentially sets aside achieving rewards by the agent for a fixed period of time at the beginning of training in favor of wild, broad exploration of the environment. Then, at an optimal time determined through tuning, all exploration is cut off in favor of exploiting what has been experienced thus far with an all out pursuit of maximum reward. My approach discards the conventional deep reinforcement learning approach which slowly shifts agents from exploring to exploiting over time and, instead, I focus the agents mainly on one task (exploration), then only the other (exploitation.)

Below are two graphs showing the improved performance of Exploratory Boost. Each had identical hyperparameters, except the noise (exploration) settings. 

<strong>Notice that in addition to faster overall convergence to the goal, Exploratory Boost also results in far fewer outlier rewards at the low end (blue that's below the yellow trend line.) The agents are experiencing far fewer poor performing episodes. They are more consistent in reaching a decent reward each time. This indicates Exploratory Boost has resulted in a higher quality of learning.</strong>

<img src="Noise_decay_method_versus_Exploratory_Boost.png">

<i>LEFT: Best result from using the traditional slow transition from explore to exploit (from OU Noise of 2.0 to 0.01 at a .9999 decay rate per episode) It reached the goal in 559 episodes. RIGHT: Best result from Exploratory Boost approach detailed below that reached the goal in 384 episodes.</i>

For Exploratory Boost I used Ornstein-Uhlenbeck noise with parameters of 0.13 theta and 0.2 sigma. I implemented a noise volume of 6 at the start of training, which mulitplied the OU noise output by 6, resulting in heavy noise and a wide variety of exploratory actions for the first 250 episodes. I then reduced the noise to zero thereafter.

### Results and Future Work


Agent is able to train in 384 episodes with average reward of 0.5 using the above hyper parameters.
