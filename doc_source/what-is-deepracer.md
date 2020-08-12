# What Is AWS DeepRacer?<a name="what-is-deepracer"></a>

AWS DeepRacer is an integrated learning system for users of all levels to learn and explore [reinforcement learning](deepracer-basic-concept.md#term-rl) and to experiment and build autonomous driving applications\. It consists of the following components:
+ AWS DeepRacer Console: an [AWS Machine Learning](https://aws.amazon.com/machine-learning/) service to [train and evaluate reinforcement learning models ](create-deepracer-project.md)in a [simulated autonomous\-driving environment](https://aws.amazon.com/robomaker/)\.
+ AWS DeepRacer Vehicle: a 1/18th scale RC car capable of [running inference on a trained AWS DeepRacer model](operate-deepracer-vehicle.md) for autonomous driving\.
+ AWS DeepRacer League: the world’s first global, autonomous racing league\. Race for prizes, glory, and a chance to advance to the Championship Cup\.

**Topics**
+ [The AWS DeepRacer Console](#what-is-deepracer-service-console)
+ [The AWS DeepRacer Vehicle](#what-is-deepracer-model-vehicle)
+ [The AWS DeepRacer League](#what-is-deepracer-racing-series)
+ [AWS DeepRacer As an Integrated Learning System](deepracer-is-a-learning-environment-for-reinforcement-learning.md)
+ [AWS DeepRacer Concepts and Terminology](deepracer-basic-concept.md)
+ [Pricing](pricing.md)

## The AWS DeepRacer Console<a name="what-is-deepracer-service-console"></a>

The AWS DeepRacer console is a graphical user interface to interact with the AWS DeepRacer service\. You can use the console to train a reinforcement learning model and to evaluate the model performance in the AWS DeepRacer simulator built upon AWS RoboMaker\. In the console, you can also download a trained model for deployment to your AWS DeepRacer vehicle for autonomous driving in a physical environment\. 

In summary, the AWS DeepRacer console supports the following features:
+ Create a training job to train a reinforcement learning model with a specified reward function, optimization algorithm, environment, and hyperparameters\. 
+ Choose a simulated track to train and evaluate a model by using Amazon SageMaker and AWS RoboMaker\.
+ Clone a trained model to improve training by tuning hyperparameters to optimize your model's performance\. 
+ Download a trained model for deployment to your AWS DeepRacer vehicle so it can drive in a physical environment\. 
+ Submit your model to a virtual race and have its performance ranked against other models in a virtual leaderboard\. 

## The AWS DeepRacer Vehicle<a name="what-is-deepracer-model-vehicle"></a>

The AWS DeepRacer vehicle is a Wi\-Fi enabled, physical vehicle that can drive itself on a physical track by using a reinforcement learning model\.
+ You can manually control the vehicle, or deploy a model for the vehicle to drive autonomously\.
+ The autonomous mode runs inference on the vehicle's compute module\. Inference uses images that are captured from the camera that is mounted on the front\. 
+ A Wi\-Fi connection allows the vehicle to download software\. The connection also allows the user to access the device console to operate the vehicle by using a computer or mobile device\.

## The AWS DeepRacer League<a name="what-is-deepracer-racing-series"></a>

 The AWS DeepRacer League League is an important component of AWS DeepRacer\. The AWS DeepRacer League is intended to foster communal learning and collaborative exploration through sharing and competition\. 

With the AWS DeepRacer League, you can have your development effort compared with other AWS DeepRacer developers in a physical or virtual racing event\. Not only do you get a chance to win prizes, you also have a way to measure your reinforcement learning model\. You can create opportunities to share your insights with other participants, to learn from each other, and to inspire each other\. 

[Join a race or learn how to train a model in the League\.](https://console.aws.amazon.com/deepracer)