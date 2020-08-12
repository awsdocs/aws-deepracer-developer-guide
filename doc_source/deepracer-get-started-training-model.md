# Train Your First AWS DeepRacer Model<a name="deepracer-get-started-training-model"></a>

To get started quickly using AWS DeepRacer to explore reinforcement learning and its application to autonomous driving, we'll walk you through how to train your first model using the AWS DeepRacer console\.<a name="deepracer-get-started-train-model-proc"></a>

**To train a reinforcement learning model using the AWS DeepRacer console**

1. If this is your first time using AWS DeepRacer, choose **Get started** from the service landing page or choose **Get started with reinforcement learning** from the main navigation pane\. 

1. On the **Get started with reinforcement learning** page, under **Step 2: Create a model and race**, choose **Create model**\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-training-create-model-on-get-started-page.png)

   Alternatively, on the AWS DeepRacer home page, choose **Your models** from the main navigation pane to open the **Your models** page\. On the **Your models** page, choose **Create model**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-training-create-model.png)

1. On the **Create model** page, under **Account resources**, if you don't have the required account resources, choose **Create resources**\. If there is any issue with the account resources, choose **Reset resources**\.

   For more information about the required IAM roles and policies, see [Required IAM Roles for AWS DeepRacer to Call Dependent AWS Services](deepracer-understand-required-permissions-and-iam-roles.md)\. 

1.  On the **Create model** page, under **Training details**, type a name for the model in **Model name** and, optionally, provide a summary description of the model in **Training job description**\.

   You'll use the model name to reference this model when submitting it to a leaderboard of an AWS\-sponsored or community\-organized racing event or when cloning to continue the training\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-training-details.png)

1. On the **Create model** page, under **Environment simulation**, choose a track as a virtual environment to train your AWS DeepRacer agent\. Then, choose **Next**\.

   For your first run, choose a track with a simple shape and smooth turns\. In later iterations, you can choose more complex tracks to progressively improve your models\. To train a model for a particular racing event, choose the track most similar to the event track\.

1. On the **Create model** page, choose **Next**\. 

1. On the **Create Model** page, under **Race type**, choose a training type\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-training-type.png)

   For your first run, choose **Time trial**\. The agent with the default sensor configuration with a single\-lens camera is suitable for this type of racing without modifications\. For more information, see [Tailor AWS DeepRacer Training for Time Trials](deepracer-choose-race-type.md#deepracer-get-started-training-simple-time-trial)\.

   For later runs, you can choose **Object avoidance** to go around stationary obstacles placed at fixed or random locations along the chosen track\. The agent should be configured with at least a double\-lens front\-facing stereo camera for such applications, although a single\-lens front\-facing camera can be used for avoiding stationary obstacles on fixed locations\. For more information, see [Tailor AWS DeepRacer Training for Object Avoidance Races](deepracer-choose-race-type.md#deepracer-get-started-training-object-avoidance)\.

    For more ambitious runs, choose **Head\-to\-head racing** to race against up to 4 bot vehicles moving at a constant speed\. In addition to either a single\-lens camera or a stereo camera, the agent should be configured with a LiDAR unit to enable detecting and avoiding blind spots while passing other moving vehicles or stationary obstacles\. For more information, see [Tailor AWS DeepRacer Training for Head\-to\-Head Races](deepracer-choose-race-type.md#deepracer-get-started-training-h2h-racing)\.

1. On the **Create model** page, under **Agent**, choose **The Original DeepRacer** for your first model\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-training-agent.png)

   The **Edit** button is unavailable because the default agent is not configurable\. For a custom agent, the **Edit** option will be available for you to modify the agent configuration to meet the racing criteria for the chosen race type\. 

1. On the **Create model** page, choose **Next**\.

1. On the **Create model** page, under **Reward function**, use the default reward function example as\-is for your first model\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-reward-function-example-editor.png)

   Later on, you can choose **Reward function examples** to select another example function and then choose **Use code** to accept the selected reward function\.

   There are four example functions you can start with\. They illustrate how to follow the track center \(default\), how to keep the agent inside the track borders, and how to prevent zig\-zag driving, and how to avoid crashing into stationary obstacles or other moving vehicles\. 

   To learn more about the reward function, see [AWS DeepRacer Reward Function Reference](deepracer-reward-function-reference.md)\.

    

1. On the **Create model** page, under **Training algorithm and hyperparameters**,  use the default hyperparameter values as\-is\.

   Later on, to improve training performance, expand **Hyperparameters** and modify the default hyperparameter values as follows:

   1.  For **Gradient descent batch size**, choose [available options](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\. 

   1.  For **Number of epochs**, set a [valid value](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\. 

   1.  For **Learning rate**, set a [valid value](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\. 

   1. For **Entropy**, set a [valid value](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\. 

   1. For **Discount factor**, set a [valid value](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\.

   1. For **Loss type**, choose [available options](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\.

   1. For **Number of experience episodes between each policy\-updating iteration**, set a [valid value](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\.

   For more information about hyperparameters, see [Systematically Tune Hyperparameters](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\.

1. On the **Create model** page, under **Stop conditions**, leave the default **Maximum time** value as\-is or set a new value to terminate the training job, to help prevent long\-running \(and possible run\-away\) training jobs\. 

   When experimenting in the early phase of training, you should start with a small value for this parameter and then progressively train for longer amounts of time\.

1. On the **Create model** page, choose **Create model** to start creating the model and provisioning the training job instance\. 

1. After the submission, watch your training job being initialized and then run\. 

   The initialization process takes about 6 minutes to change status from **Initializing** to **In progress**\.

1. Watch the **Reward graph** and **Simulation video stream** to observe the progress of your training job\. You can choose the refresh button next to **Reward graph** periodically to refresh the **Reward graph** until the training job is complete\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-training-in-progress.png)

The training job is running on the AWS Cloud, so you don't need to keep the AWS DeepRacer console open during training\. However, you can come back to the console to check on your model at any point while the job is in progress\. 

If the** Simulation video stream** window or the **Reward graph** display becomes unresponsive, refresh the browser page to get the training progress updated\.

After the training job stops, you can proceed to evaluate the model trained thus far\. To do so, follow the next [steps](deepracer-get-started-test-in-simulator.md)\.