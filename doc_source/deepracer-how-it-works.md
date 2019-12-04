# How AWS DeepRacer Works<a name="deepracer-how-it-works"></a>

 AWS DeepRacer vehicle is a 1/18th scale vehicle that can autonomously drive along a track by itself or race against another vehicle\. The vehicle can be equipped with various sensors that include a front\-facing camera, stereo cameras, radars or a LiDAR\. The sensors collect data about the environment the vehicle operates in\. Different sensors provide the view at different scales\. 

 AWS DeepRacer uses reinforcement learning to enable autonomous driving for the AWS DeepRacer vehicle\. To achieve this, you train and evaluate a reinforcement learning model in a virtual environment with a simulated track\. After the training, you upload the trained model artifacts to your AWS DeepRacer vehicle\. You can then set the vehicle for autonomous driving in a physical environment with a real track\. 

 Training a reinforcement learning model can be challenging, especially if you're new to the field\. AWS DeepRacer simplifies the process by integrating required components together and providing easy\-to\-follow wizard\-like task templates\. However, it's helpful to have a good understanding of the basics of reinforcement learning training implemented in AWS DeepRacer\. 

**Topics**
+ [Reinforcement Learning in AWS DeepRacer](deepracer-how-it-works-overview-reinforcement-learning.md)
+ [AWS DeepRacer Action Space and Reward Function](deepracer-how-it-works-action-space.md)
+ [AWS DeepRacer Training Algorithm](deepracer-how-it-works-reinforcement-learning-algorithm.md)
+ [AWS DeepRacer Service Architecture](deepracer-how-it-works-service-architecture.md)
+ [AWS DeepRacer Solution Workflow](deepracer-how-it-works-solution-workflow.md)
+ [Simulated\-to\-Real Performance Gaps](deepracer-how-it-works-virtual-to-physical.md)