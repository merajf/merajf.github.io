##CartPole-v0 environment in OpenAI Gym

1.	Problem Statement
The CartPole must balance on the trolley for 200 steps for 20 consecutive episodes, with the training occurring in the least possible number of episodes using a Deep Q Network (DQN).
 

2.	Modelling
After importing the necessary libraries, below were the main models created after tuning different parameters, but the deep neural network used remain the same throughout. 
All models mentioned in this report have a 0.2 eps value and the same learning rate. Both values were obtained after trying out different values. By setting the eps value to 0.2, it implies a 20% probability of exploration (RexCoding, 2022). In doing so, we seek to set the balance between exploration and exploitation carried out by the agent.
 	 

Warmups and Gamma
It was found if the number of warmup steps were too small, it will take the agent longer to achieve the goal. Since nb_steps_warmup determines how long to wait before experience replay is started, this would be in effect be similar to setting the batch size. So, setting it as 10 as opposed to 55, when the total number of steps was set as 10,000 might be unnecessarily small and thereby hurting the performance of the agent.    
10 warmup steps and no gamma value	55 warmup steps and 0.99 gamma value

 	
 
 	 

A few different gamma values close to 1 were tried. The gamma value is the discount factor which determines the present value of future rewards (PyTorch, 2023). While it is not clear why a value as high as 0.99 yielded better results, given the task is to have a set number of rewards for 20 steps, it makes intuitive sense why a low value would yield worse results as the agent would be more concerned with maximizing immediate rewards.
The model with 0.99 gamma value and 55 warmup steps reached the goal significantly faster and recorded no period of stagnation.

Total nb_steps
	Previously, the number of nb_steps for training the model was set as 10,000 arbitrarily. From previous experimentations with warmups, it is understood how the agent learns in terms of batch size has an impact in accomplishing the task. With that in mind, a few different numbers for nb_steps were tried and 6000 yielded the best results.
 
 



3.	References

1.	RexCoding (2022) Reinforcement Learning for Engineers in a Hurry. Available at: https://de-fellows.github.io/RexCoding/machine%20learning/reinforcement%20learning/neural%20networks/2022/05/31/Reinforcement-Learning.html.
[Accessed 20 Mar 2023]

2.	PyTorch (2023) Reinforcement Learning (DQN) Tutorial — PyTorch Tutorials documentation. Available at: https://pytorch.org/tutorials/intermediate/reinforcement_q_learning.html.
[Accessed 20 Mar 2023]
