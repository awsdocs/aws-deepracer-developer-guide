# AWS DeepRacer Concepts and Terminology<a name="deepracer-basic-concept"></a>

 AWS DeepRacer builds on the following concepts and uses the following terminology\.

**AWS DeepRacer**  <a name="term-deepracer"></a>
Also referred to as AWS DeepRacer vehicle\. One type of AWS DeepRacer vehicle is an AWS DeepRacer car that is a 1/18th scale model car\. It has a mounted camera and an on\-board compute module\. The compute module runs inference in order to drive itself along a track\. The compute module and the vehicle chassis are powered by dedicated batteries known as the compute battery and the drive battery, respectively\. 

**AWS DeepRacer service**  <a name="term-deepracer-service"></a>
An AWS Machine Learning service for exploring reinforcement learning that is focused on autonomous racing\. The AWS DeepRacer service supports the following features:  

1. Train a reinforcement learning model on the cloud\. 

1. Evaluate a trained model in the AWS DeepRacer console\.

1. Submit a trained model to a virtual race and, if qualified, have its performance posted to the event's leaderboard\.

1. Clone a trained model continue training for improved performances\.

1. Download the trained model artifacts for uploading to an AWS DeepRacer vehicle\.

1. Place the vehicle on a physical track for autonomous driving and evaluate the model for real\-world performances\. 

1. Run the AWS DeepRacer League for racing events on physical tracks\.

1. Remove unnecessary charges by deleting models that you don't need\.

**Reinforcement learning**  <a name="term-rl"></a>
A machine learning method that is focused on autonomous decision making by an agent in order to achieve specified goals through interactions with an environment\. In reinforcement learning, learning is achieved through trial and error and training does not require labeled input\. Training relies on the reward hypothesis\. The hypothesis is that all goals can be achieved by maximizing a future reward after action sequences\. In reinforcement learning, designing the reward function is important\. The better the reward function is crafted, the better the agent can decide what actions to take to reach the goal\.  
For autonomous racing, the agent is a vehicle\. The environment includes traveling routes and traffic conditions\. The goal is for the vehicle to reach its destination quickly without accidents\. Rewards are scores used to encourage safe and speedy travel to the destination\. The scores penalize dangerous and wasteful driving\.   
To encourage learning during training, the learning agent must be allowed to sometimes pursue actions that might not result in rewards\. This is referred to as the exploration and exploitation trade\-off\. It helps reduce or remove the likelihood that the agent might be misguided into false destinations\.   
For a more formal definition, see [reinforcement learning](https://en.wikipedia.org/wiki/Reinforcement_learning) on Wikipedia\.

**Reinforcement learning model**  <a name="term-rl-model"></a>
The environment in which an agent acts establishes three things: The states that the agent has, the actions that the agent can take, and the rewards that are received by taking action\. The strategy with which the agent decides its action is referred to as a policy\. The policy takes the environment state as input and outputs the action to take\. In reinforcement learning, the policy is often represented by a deep neural network and we refer to this as the reinforcement learning model\. Each training job generates one model\. A model can be generated even if the training job is stopped early\. A model is immutable, which means it cannot be modified and overwritten after it's created\. 

**AWS DeepRacer simulator**  <a name="term-simulator"></a>
A virtual environment built on AWS RoboMaker for visualizing training and evaluating AWS DeepRacer models\. 

**AWS DeepRacer vehicle**  <a name="term-model-vehicle"></a>
See [AWS DeepRacer](#term-deepracer)

**AWS DeepRacer car**  <a name="term-deepracer-car"></a>
A type of [AWS DeepRacer vehicle](#term-model-vehicle) that is a 1/18th scale model car\.

**Leaderboard**  <a name="term-leaderboard"></a>
A *leaderboard* is a ranked list of AWS DeepRacer vehicle performances in an AWS DeepRacer League racing event\. The race can be a virtual event, carried out in the simulated environment, or a physical event, carried out in a real\-world environment\. The performance metric is the average lap time submitted by AWS DeepRacer users who have evaluated their trained models on a track identical or similar to the given track of the race\.    
If a vehicle completes three laps consecutively, then it qualifies to be ranked on a leaderboard\. The average lap time for the first three consecutive laps is submitted to the leaderboard\. 

**Machine\-learning frameworks**  <a name="term-frameworks"></a>
The software libraries used to build machine learning algorithms\. Supported frameworks for AWS DeepRacer include Tensorflow\.

**Policy network**  <a name="term-policy-network"></a>
A policy network is a neural network that is trained\. The policy network takes video images as input and predicts the next action for the agent\. Depending on the algorithm, it may also evaluate the value of current state of the agent\. 

** Optimization algorithm**  <a name="term-optimization-algorithm"></a>
An optimization algorithm is the algorithm used to train a model\. For supervised training, the algorithm is optimized by minimizing a loss function with a particular strategy to update weights\. For reinforcement learning, the algorithm is optimized by maximizing the expected future rewards with a particular reward function\.

**Neural network**  
A collection of connected units or nodes that are used to build an information model based on biological systems\. Also referred to as artificial neural network\. Each node is called an artificial neuron and mimics a biological neuron in that it receives an input \(stimulus\), becomes activated if the input signal is strong enough \(activation\), and produces an output predicated upon the input and activation\. It’s widely used in machine learning because an artificial neural network can serve as a general\-purpose approximation to any function\. Teaching machine to learn becomes finding the optimal function approximation for the given input and output\. In deep reinforcement learning, the neural network represents the policy and is often referred to as the policy network\. Training the policy network amounts to iterating through steps that involve generating experiences based on the current policy followed by optimizing the policy network with the newly generated experiences\. The process continues until certain performance metrics meet required criteria\. 

** Hyperparameters**  <a name="term-hyperparameters"></a>
Algorithm\-dependent variables that control the performance of training a neural network\. An example hyperparameter is the learning rate that controls how much new experiences are counted for in learning at each step\. A larger learning rate makes a faster training but may make the trained model lower quality\. Hyperparameters are empirical and require systematic tuning for each training\. 

**AWS DeepRacer Track**  <a name="term-track"></a>
A path or course on which an AWS DeepRacer vehicle drives\. The track can exist in either a simulated or real\-world, physical environment\. You use a simulated environment for training an AWS DeepRacer model on a virtual track\. The AWS DeepRacer console makes virtual tracks available\. You use a real\-world environment for running an AWS DeepRacer vehicle on a physical track\. The AWS DeepRacer League provides physical tracks for event participants to compete\. You must create your own physical track if you want to run your AWS DeepRacer vehicle in any other situation\.

** Reward function**  <a name="term-reward-function"></a>
An algorithm within a learning model that tells the agent whether the action performed resulted in:  
+ A good outcome that should be reinforced\.
+ A neutral outcome\.
+ A bad outcome that should be discouraged\.
The reward function is a key part of reinforcement learning\. It determines the behavior that the agent learns by incentivizing specific actions over others\. The user provides the reward function by using Python\. This reward function is used by an optimizing algorithm to train the reinforcement learning model\.

**Experience episode**  <a name="term-episode"></a>
A period in which the agent collects experiences as training data from the environment by running from a given starting point to completing the track or going off the track\. Different episodes can have different lengths\. Also referred to as an episode or experience\-generating episode\. 

** Experience iteration**  
Consecutive experiences between each policy iteration that performs updates of the policy network weights\. Also referred to as an experience\-generating iteration, the size can be set in one of the hyperparameters for training\. At the end of each experience iteration, the collected episodes are added to an experience replay or buffer\. The neural network is updated by using random samples of the experiences\.

**Policy iteration**  
Any number of passes through the randomly sampled training data to update the policy neural network weights during gradient ascent\. A single pass through the training data to update the weights is also known as an epoch\. Policy iteration is also referred to as policy\-updating iteration\.

**Training job**  <a name="term-training-job"></a>
A workload that trains a reinforcement learning model and creates trained model artifacts on which to run inference\. Each training job has two sub\-processes:   

1. Start the agent to follow the current policy\. The agent explores the environment in a number of [*episodes*](#term-episode) and creates training data\. This data generation is an iterative process itself\.

1. Apply the new training data to compute new policy gradients\. Update the network weights and continue training\. Repeat Step 1 until a stop condition is met\.
Each training job produces a trained model and outputs the model artifacts to a specified data store\. 

**Evaluation job**  <a name="term-evaluation-job"></a>
A workload that tests the performance of a model\. Performance is measured by given metrics after the training job is done\. The standard AWS DeepRacer performance metric is the driving time that an agent takes to complete a lap on a track\. Another metric is the percentage of the lap completed\. 

## Racing Event Terminology<a name="racing-event-terminology"></a>

**League/Competition**  
In the context of AWS DeepRacer League events, the terms league and competition relate to the competition structure\. AWS sponsors the AWS DeepRacer League, which means we own it, design it, and execute it\. A competition has a start and end date\.

**Season**  
A competition can repeat in subsequent years\. We call these different seasons \(for example, the 2019 season or 2020 season\)\. Rules can change from season to season, but are typically consistent within a season\. Terms and conditions for the AWS DeepRacer League can vary from season to season\.

**Circuit**  
In the AWS DeepRacer League, you can choose to race in the Summit Circuit or in the Virtual Circuit\. The Summit Circuit refers to in\-person races happening at selected AWS Summits\. The Virtual Circuit refers to the online races happening in the AWS DeepRacer console\.

**Event**  
As defined by the rules, an event is an AWS DeepRacer League occurance where you can participate in a race\. It can be in\-person, like the Summit Circuit, or online, like the virtual circuit\. An event has a start and end date\. Virtual Circuit events will typically last a month, whereas Summit Circuit events will typically last a day\. There can be many events in a season, and some rules, such as how we rank those participating in an event, select who wins, and what happens thereafter are subject to change\.

**Race type**  
There are flexible options for race types available at each event\. In the Summit Circuit, you can choose to race in a time\-trial \(TT\) race, or in a head\-to\-head \(H2H\) race, or both\. In the Virtual Circuit, you can race in a time\-trial \(TT\), object\-avoidance \(OA\), or head\-to\-head \(H2H\) race, or all three\. Beginning in 2020, the default Virtual Circuit program includes TT, OA, and H2H\. However, we may add a fourth bonus race at a particular event\. Alternatively, an event host could choose to only offer a TT race\. Each race type may also specify the number of laps, how racers are ranked and so on\.