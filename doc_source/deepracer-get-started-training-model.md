# Train Your First AWS DeepRacer Model for Autonomous Racing<a name="deepracer-get-started-training-model"></a>

Using the AWS DeepRacer console, you can follow built\-in templates to train and evaluate an AWS DeepRacer model\. <a name="deepracer-get-started-train-model-proc"></a>

**To train a reinforcement learning model for autonomous racing using the AWS DeepRacer console**

1. Sign in to the [AWS DeepRacer console](https://console.aws.amazon.com/deepracer) \(https://console\.aws\.amazon\.com/deepracer\)\.

1. On the AWS DeepRacer home page, choose **Get started** and do the following on the **Get started with reinforcement learning** page:

   1. Under **Account resources**, choose **Create resources**, if this is your first time to use AWS DeepRacer\. 

   1. If you're new reinforcement learning, choose **Learn RL** under **Introduction to reinforcement learning** to get familiar with reinforcement learning\.

   1. Under **Create a reinforcement learn \(RL\) model**, choose **Create model** to start to create your first AWS DeepRacer model\.

   If you have prior experiences with AWS DeepRacer, you can skip this step and choose instead **Reinforcement learning** on the primary navigation pane and then choose **Create model**\.

1.  On the **Create model** page, do the following to configure and start training your AWS DeepRacer model: 

   1. To refresh your account resources, choose **Reset resources** under **Account resources**\. This action forces the required resources for your account to be recreated or re\-associated\. 

      When the required resources are created, you should see the following display:  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-resources-created.png)

      The Amazon S3 bucket is used to store the trained model artifacts\. And the IAM roles contain relevant IAM policies to grant AWS DeepRacer permission to call other AWS services on your behalf\. For more information about the required IAM roles and policies, see [Required IAM Roles for AWS DeepRacer to Call Dependent AWS Services](deepracer-understand-required-permissions-and-iam-roles.md)\. The AWS DeepRacer Virtual Private Cloud \(VPC\) stack is used to run training jobs\. The AWS RoboMaker simulation application is used to visualize training and evaluating your model\.

   1.  Under **Model details**, enter a name for the to\-be\-trained model in the **Model name** input field and optionally provide a brief description in the **Model description \- optional** input field\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-train-model.png)

      The model name identifies this model among the AWS DeepRacer models you've created and on the leaderboards, which show the performance rank of the model\. The model description can provide a summary of the model features and limitations\.

   1. Under **Environment simulation**, choose an available track as a virtual environment to train your AWS DeepRacer model through trials and errors\. For your first run, choose a simple option, e\.g\., of **Straight track**\. In later iterations, you can choose more complex track to progressively improve your models\. To train a model for a particular racing event, choose a track most similar to the track of the event\.

   1. Under **Action space**, use the default setting for your first training\. Later, you can explore different size and granularity of the action space to make your model sufficiently flexible to accommodate the selected track\.

   1.  Under **Reward function**, use the default reward function example or choose **Reward function examples** to select another example function and then choose **Use code** of the selected function\. 

      There are three example functions you can start with\. They illustrate how to follow the track center \(default\), how to keep the agent inside the track borders, and how to prevent zig\-zag driving\. 

      After getting familiar with the reward function examples, you can modify or replace the predefined reward function code in the code editor\.

   1. Under **Hyperparameters**, you can leave the default values or expand the section to set **Hyperparameters** values as follows: 

      1.  For **Gradient descent batch size**, choose [available options](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\. 

      1.  For **Number of epochs**, set a [valid value](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\. 

      1.  For **Learning rate**, set a [valid value](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\. 

      1. For **Entropy**, set a [valid value](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\. 

      1. For **Discount factor**, set a [valid value](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\.

      1. For **Loss type**, choose [available options](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\.

      1. For **Number of experience episodes between each policy\-updating iteration**, set a [valid value](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\.

      For more information about hyperparameters, see [Systematically Tune Hyperparameters](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters)\.

   1. Under **Stop conditions**, set a **Maximum time** value to terminate long\-running \(and possible run\-away\) training session\.

   1.  Choose **Start training** to start creating the model and provisioning the training job instance\. 

1.  A training starts with provisioning a AWS DeepRacer training job\. The process takes about 6 minutes and its status is **Initializing** until the training job is successfully provisioned\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-training-status.png)

1. After the job is provisioned, training starts and the process has **In progress** status until the job stops\. You can choose the refresh button to periodically refresh the **Reward graph**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-training-in-progress.png)

1. After the training job stops, the process is **Completed**, and you can start to [evaluate your trained model](deepracer-get-started-test-in-simulator.md) to measure its performance\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-training-completed.png)

    