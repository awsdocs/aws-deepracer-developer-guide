# AWS DeepRacer Service Architecture<a name="deepracer-how-it-works-service-architecture"></a>

The AWS DeepRacer service is built upon [Amazon SageMaker](https://aws.amazon.com/sagemaker), [AWS RoboMaker](https://console.aws.amazon.com/robomaker) and other AWS services such as [Amazon S3](https://console.aws.amazon.com/s3)\. 

Amazon SageMaker is an AWS machine learning platform to train machine learning models in general\. AWS DeepRacer uses it to train reinforcement learning model in particular\. AWS RoboMaker is a cloud service to develop, test and deploy robotic solutions in general\. AWS DeepRacer uses it create the virtual agent and its interactive environment\. Amazon S3 is an economical general\-purpose cloud storage solution\. AWS DeepRacer uses it to store trained model artifacts\. In addition, AWS DeepRacer uses [Redis](https://redis.io), an in\-memory database, as an experience buffer to select training data from for training the policy neural network\.

Within the AWS DeepRacer architecture, AWS RoboMaker creates a simulated environment for the agent to drive along a specified track\. The agent moves according to the policy network model that has been trained up to a certain time in Amazon SageMaker\. Each run starts from the starting line to an end state which can be the finishing line or off the track and is known as an episode\. For each episode, the course is divided into segments of a fixed number of steps\. In each segment experiences, defined as an ordered list of the tuples of \(*state*, *action*, *reward*,* new state*\) associated with individual steps, are cached in Redis as an experience buffer\. Amazon SageMaker then randomly draws from the experience buffer training data in batches and feeds the input data to the neural network to update the weights\. It then stores the updated model in Amazon S3 for Amazon SageMaker to use in order to generate more experiences\. The cycle continues until training stops\.

In the beginning before the first model is trained for the first time, Amazon SageMaker initializes the experience buffer with random actions\.

The following diagram illustrates this architecture\.

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-architecture.png)

This setup allows running multiple simulations to train a model on multiple segments of a single track at the same time or to train the model for multiple tracks simultaneously\. 