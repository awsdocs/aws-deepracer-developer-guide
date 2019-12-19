# AWS DeepRacer Action Space and Reward Function<a name="deepracer-how-it-works-action-space"></a>

For autonomous driving, the AWS DeepRacer vehicle receives input images streamed at 15 frames per second from the front camera\. The raw input is downsized to 160x120 pixels in size and converted to grayscale images\. 

Responding to an input observation, the vehicle reacts with a well\-defined action of specific speed and steering angle\. The actions are converted to low\-level motor controls\. The possible actions a vehicle can take is defined by an action space of the dimensions in speed and steering angle\. An action space can be discrete or continuous\. AWS DeepRacer uses a discrete action space\. 

For a discrete action space of finite actions, the range is defined by the maximum speed and the absolute value of the maximum steering angles\. The granularities define the number of speeds and steering angles the agent has\.

For example, the AWS DeepRacer default action space has the following actions you can use to train an AWS DeepRacer model\. 


**The default AWS DeepRacer action space**  

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

This default action space is characterized by the following ranges and granularities:


**The default action space characteristics**  

| Property | Value | 
| --- | --- | 
| Maximum steering angle | 30 degrees | 
| Steering angle granularity | 5 | 
| Maximum speed | 0\.8 m/s | 
| Speed granularity | 2 | 

To influence behavior, we can explore a reward function to assign immediate rewards to the actions in this action space\. For example, AWS DeepRacer has a basic reward function by default to encourage the agent to stay as close to the center line as possible\. The agent avoids steering close to the edge of the track and going off the track with even a slight turn\. For details of this default reward function in the AWS DeepRacer console, see [AWS DeepRacer reward function example](deepracer-reward-function-examples.md#deepracer-reward-function-example-0)\. 

In addition to the default action space, you can also explore a [custom action space](deepracer-console-train-evaluate-models.md#deepracer-define-action-space-for-training) and a [custom reward function](deepracer-console-train-evaluate-models.md#deepracer-train-models-define-reward-function) to train your models\.

You can apply a trained model to an AWS DeepRacer vehicle by mapping the maximum speed \(*0\.8 m/s*\) and maximum steering angles \(*30 degrees*\) used in training to the corresponding maximum physical values\. This is called [vehicle calibration](deepracer-calibrate-vehicle.md)\. 