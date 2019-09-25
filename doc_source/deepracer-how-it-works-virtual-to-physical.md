# Simulated\-to\-Real Performance Gaps<a name="deepracer-how-it-works-virtual-to-physical"></a>

Because the simulation cannot capture all aspects of the real world accurately, the models trained in simulation may not work well in the real world\. Such discrepancies are often referred to as simulated\-to\-real \(*sim2real*\) performance gaps\. 

Efforts have been made in AWS DeepRacer to minimize the *sim2real* performance gap\. For example, the simulated agent is programmed to take about 10 actions per second\. This matches the frequency the AWS DeepRacer vehicle runs inference with, about 10 inferences per second\. As another example, at the start of each episode in training, the agent's position is randomized\. This maximizes the likelihood that the agent learns all parts of the track evenly\. 

 To help reduce *real2sim* performance gaps, make sure to use the same or similar color, shape and dimensions for both the simulated and real tracks\. To reduce visual distractions, use barricades around the real track\. Also, carefully calibrate the ranges of the vehicle's speed and steering angles so that the action space used in training matches the real world\. Evaluating model performance in a different simulation track than the one used in training can show the extent of the *real2real* performance gap\. 

For more information about how to reduce the *sim2real* gap when training an AWS DeepRacer model, see [Optimize Training AWS DeepRacer Models for Real Environments](deepracer-console-train-evaluate-models.md#deepracer-evaluate-model-test-approaches)\.