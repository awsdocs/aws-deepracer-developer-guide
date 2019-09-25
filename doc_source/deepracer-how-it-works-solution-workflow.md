# AWS DeepRacer Solution Workflow<a name="deepracer-how-it-works-solution-workflow"></a>

Training an AWS DeepRacer model involves the following general tasks: 

1. The AWS DeepRacer service initializes the simulation with a virtual track, an agent representing the vehicle, and the background\. The agent embodies a policy neural network that can be tuned with hyper\-parameters as defined in the [PPO algorithm](deepracer-how-it-works-reinforcement-learning-algorithm.md)\. 

1. The agent acts \(as specified with a steering angle and a speed\) based on a given state \(represented by an image from the front camera\)\.

1. The simulated environment updates the agent's position based on the agent action and returns a reward and an updated camera image\. The experiences collected in the form of state, action, reward, and new state are used to update the neural network periodically\. The updated network models are used to create more experiences\. 

1. You can monitor the training in progress along the simulated track with a first\-person view as seen by the agent\. You can display metrics such as rewards per episode, the loss function value, the entropy of the policy\. CPU or memory utilization can also be displayed as training progresses\. In addition, detailed logs are recorded for analysis and debugging\. 

1. The AWS DeepRacer service periodically saves the neural network model to persistent storage\. 

1. The training stops based on a time limit\. 

1. You can evaluate the trained model in a simulator\. To do this submit the trained model for time trials for a selected number runs on the selected track\. 

 After the model is successfully trained and evaluated, it can be uploaded to a physical agent \(an AWS DeepRacer vehicle\)\. The process involves the following steps:

1. Download the trained model from its persistent storage \(an Amazon S3 bucket\)\.

1. Use the vehicle's device control console to upload the trained model to the vehicle\. Use the console to calibrate the vehicle for mapping the simulated action space to the physical action space\. You can also use the console to check the throttling parity, view the front camera feed, load a model into the inference engine, and watch the vehicle driving on a real track\. 

   The vehicle's device control console is a web server hosted on the vehicle's compute module\. The console is accessible from the vehicle IP address with a connected Wi\-Fi network and a web browser on a computer or a mobile device\.

1. Experiment with the vehicle driving under different lighting, battery levels, and surface textures and colors\. 

   The vehicle's performance in a physical environment may not match the performance in a simulated environment due to model limitations or insufficient training\. The phenomenon is referred to as the *sim2real* performance gap\. To reduce the gap, see [Simulated\-to\-Real Performance Gaps](deepracer-how-it-works-virtual-to-physical.md)\.