# AWS DeepRacer Action Space and Reward Function<a name="deepracer-how-it-works-action-space"></a>

**Action Space**  
In reinforcement learning, the set of all valid actions, or choices, available to an agent as it interacts with an environment is called an action space\. In the AWS DeepRacer console, you can train agents in either a discrete or continuous action space\.

**Discrete Action Space**  
A discrete action space represents all of an agent's possible actions for each state in a finite set\. For DeepRacer, this means that for every incrementally different environmental situation, the agent's neural network selects a speed and direction for the car based on input from its camera\(s\) and \(optional\) LiDAR sensor\. The choice is limited to a grouping of predefined steering angle and throttle value combinations\.

A DeepRacer car in a discrete action space approaching a turn can choose to accelerate or break and turn left, right, or go straight\. These actions are defined as a combination of steering angle and speed creating a menu of options, 0\-9, for the agent\. For example, 0 could represent \-30 degrees and 0\.4 m/s, 1 could represent \-30 degrees and 0\.8 m/s, 2 could represent \-15 degrees and 0\.4 m/s, 3 could represent \-15 degrees and 0\.8 m/s and so on through 9\. Negative degrees turn the car right, positive degrees turn the car left and 0 keeps the wheels straight\.

The AWS DeepRacer default discrete action space contains the following actions:


**AWS DeepRacer default discrete action space**  

| Action number | Steering | Speed | 
| --- | --- | --- | 
| 0 | \-30 degrees | 0\.4 m/s | 
| 1 | \-30 degrees | 0\.8 m/s | 
| 2 | \-15 degrees | 0\.4 m/s | 
| 3 | \-15 degrees | 0\.8 m/s | 
| 4 | 0 degrees | 0\.4 m/s | 
| 5 | 0 degrees | 0\.8 m/s | 
| 6 | 15 degrees | 0\.4 m/s | 
| 7 | 15 degrees | 0\.8 m/s | 
| 8 | 30 degrees | 0\.4 m/s | 
| 9 | 30 degrees | 0\.8 m/s | 

**Continuous Action Space**  
A continuous action space allows the agent to select an action from a range of values for each state\. Just as with a discrete action space, this means for every incrementally different environmental situation, the agent's neural network selects a speed and direction for the car based on input from its camera\(s\) and \(optional\) LiDAR sensor\. However, in a continuous action space, you can define the range of options the agent picks its action from\.

In this example, the DeepRacer car in a continuous action space approaching a turn can choose a speed from 0\.75 m/s to 4 m/s and turn left, right, or go straight by choosing a steering angle from \-20 to 20 degrees\.

**Discrete vs\. continuous**  
The benefit of using a continuous action space is that you can write reward functions that train models to incentivize speed/steering actions at specific points on a track that optimize performance\. Picking from a range of actions also creates the potential for smooth changes in speed and steering values that, in a well trained model, may produce better results in real\-life conditions\.

In the discrete action space setting, limiting an agent's choices to a finite number of predefined actions puts the onus on you to understand the impact of these actions and define them based on the environment \(track, racing format\) and your reward functions\. However, in a continuous action space setting, the agent learns to pick the optimal speed and steering values from the min/max bounds you provide through training\.

Though providing a range of values for the model to pick from seems to be the better option, the agent has to train longer to learn to choose the optimal actions\. Success is also dependent upon the reward function definition\.

**Reward Function**  
As the agent explores the environment, the agent learns a value function\. The value function helps your agent judge how good an action taken is, after observing the environment\. The value function uses the reward function that you write in the AWS DeepRacer console to score the action\. For example, in the follow the center line sample reward function in the AWS DeepRacer console, a good action would keep the agent near the center of the track and be scored higher than a bad action, which would move the agent away from the center of the track\.

Over time, the value function helps the agent learn policies that increase the total reward\. The optimal, or best policy, would balance the amount of time the agent spends exploring the environment with the amount of time it spends exploiting, or making the best use of, what the policy has learned through experience\.

In the follow the center line [AWS DeepRacer sample reward function example](deepracer-reward-function-examples.md#deepracer-reward-function-example-0), the agent first takes random actions to explore the environment, which means it doesn't do a very good job of staying in the center of the track\. Over time, the agent begins to learn which actions keep it near the center line, but if it does this by continuing to take random actions, it will take a long time to learn to stay near the center of the track for the entire lap\. So, as the policy begins to learn good actions, the agent begins to use those actions instead of taking random actions\. However, if it always uses or exploits the good actions, the agent won't make any new discoveries, because it's no longer exploring the environment\. This trade\-off is often referred to as the exploration vs exploitation problem in RL\.

Experienment with the default action spaces and sample reward functions\. Once you've explored them all, exploit your knowledge by designing your own [custom action spaces](deepracer-console-train-evaluate-models.md#deepracer-define-action-space-for-training) and [custom reward functions](deepracer-console-train-evaluate-models.md#deepracer-train-models-define-reward-function)\.
