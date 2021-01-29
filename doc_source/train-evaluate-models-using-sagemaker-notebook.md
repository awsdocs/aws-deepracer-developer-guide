# Train and Evaluate AWS DeepRacer Models Using SageMaker Notebooks<a name="train-evaluate-models-using-sagemaker-notebook"></a>

 The AWS DeepRacer console provides you with an integrated experience to train and evaluate your AWS DeepRacer models\. It's integrated because AWS DeepRacer uses SageMaker and AWS RoboMaker behind the scenes\. The integration includes detailed reinforcement learning tasks and makes training more readily accessible to beginners\. 

 If you're an experienced user of SageMaker or if you're determined to learn how to use SageMaker and AWS RoboMaker to train and evaluate your AWS DeepRacer models, then you can manually create an SageMaker notebook\. You can then clone a reinforcement learning sample notebook instance and use it as a template to perform the predefined tasks that train and evaluate an AWS DeepRacer model\. 

After the training, you can copy the trained model artifacts to your AWS DeepRacer vehicle for test runs in a physical environment\. 

The tutorial presents step\-by\-step instructions to walk you through these tasks\. 

**Topics**
+ [Create an SageMaker Notebook](#train-evaluate-models-using-sagemaker-notebook-create)
+ [Initialize the SageMaker Notebook Instance](#train-evaluate-models-using-sagemaker-notebook-initialize-instance)
+ [Set Up the Training Environment](#train-evaluate-models-using-sagemaker-notebook-set-up-environment)
+ [Train Your AWS DeepRacer Model](#train-evaluate-models-using-sagemaker-notebook-train-model)

## Create an SageMaker Notebook<a name="train-evaluate-models-using-sagemaker-notebook-create"></a>

To train an AWS DeepRacer model directly on SageMaker, follow the steps below and create an SageMaker notebook instance\. 

**To create an SageMaker notebook instance to train and evaluate your AWS DeepRacer models**

1.  Sign in to the SageMaker console at [https://console\.aws\.amazon\.com/sagemaker](https://console.aws.amazon.com/sagemaker)\. Choose one of the supported regions\. 

1.  From the navigation pane, choose **Notebook instances** and then choose **Create notebook instance**\. 

1.  On the **Create notebook instance** page, do the following: 

   1. Type a name\. For example, `my-deepracer-model`\) for the **Notebook instance name**\.

   1. If the **IAM role** drop\-down menu is not populated with an existing IAM role, choose **Create a new role**, **Enter a custom IAM role ARN**, or **Use existing role** and then follow the instructions\.

   1.  Leave the default choices for all other options and then choose **Create notebook instance**\. 

    For more information, see [creating an SageMaker notebook instance](https://docs.aws.amazon.com/sagemaker/latest/dg/gs-setup-working-env.html)\. 

1.  Wait for the notebook instance's **Status** to change from `Pending` to `InService`\. Then choose **Open Jupyter**\. 

1.  On the **Jupyter** page \(which is the home page of the newly created notebook\), do the following:

   1.  Choose the **SageMaker Examples** tab\. 

   1.  Expand the **Reinforcement Learning** example group from the example collection\. 

   1.  For this exercise, choose **Use** next to the **deepracer\_rl\.ipynb** item\. 

   1.  On the **Create a copy in your home directory** dialog, choose **Create copy**\. 

   At this point, the notebook instance is running and you can begin to train the model\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-start-page.png)

    You are charged for a running instance according to the selected instance type\. To avoid being charged for a running instance when you're not ready to use it, shut down the instance\.

 

## Initialize the SageMaker Notebook Instance<a name="train-evaluate-models-using-sagemaker-notebook-initialize-instance"></a>

 To use an SageMaker notebook instance to train your AWS DeepRacer model, first properly initialize the instance for the required job\. The initialization includes the following\. 
+ Import required libraries\.
+ Set up training environment\.
+ Grant access permissions for SageMaker and AWS RoboMaker\.
+ Provision a docker container to host training and evaluation jobs\.
+ Configure VPC for SageMaker and AWS RoboMaker to interact with each other\.

Follow the steps below for detailed instructions to initialize a notebook instance\.

**To initialize an SageMaker notebook instance**

1. To import the required library to do training, choose the notebook instance's first code block\. For example, choose the one under the **Imports** heading\. Next, choose **Run** from the notebook's menu bar to execute the code block\. You can use the `Shift-Enter` key\-command shortcuts to start running the code block\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-initialize-import.png)

   Before the code execution starts, the code block status shows `In [ ]`\. When the execution is under way, the status becomes `In [*]`\. After the code execution is complete, the status becomes `In [n]`, where *`n`* corresponds to the order of invocations\. Because the importation code cell is the first, `n=1`\. If you run the command again after the first run, the status becomes `In [2]`\.

   For asynchronous execution, the code cell returns immediately to show the completed status\. For synchronous executions, subsequent calls are blocked until the current code cell execution is completed when the status turns from `In [*]` to `In [n]`\.

1. To initialize the basic parameters, run the **Initializing basic parameters** code block as\-is\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-initialize-basic-parameters.png)

   The example notebook instance sets the job duration for 1 hour by default\. To speed up or extend the training, you can decrease or increase the `job_duration_in_seconds` value before running the code cell\. 

1.  To set up the training output storage, choose the code block under **Setup S3 bucket**, and then choose **Run** from the notebook instance menu or press the `Shift+Enter` keys\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-initialize-s3-bucket.png)

   When the execution completes, you can verify this bucket in Amazon S3 console\. 

   To view the `s3_output_path` variable value, append `print(s3_output_path)` to the above code cell and rerun the code\.

1. To set up appropriate permissions for this notebook instance to access the S3 storage for output by SageMaker, run the code cell under **Create an IAM role**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-initialize-create-iam-role.png)

   When executed, this code block creates a new IAM role containing the following IAM policy\.

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Effect": "Allow",
               "Action": [
                   "s3:GetObject",
                   "s3:PutObject",
                   "s3:DeleteObject",
                   "s3:ListBucket"
               ],
               "Resource": [
                   "arn:aws:s3:::*"
               ]
           }
       ]
   }
   ```

   The created IAM role has SageMaker as its trusted entity\. 

1. To set up appropriate permissions for this notebook instance to invoke AWS RoboMaker to simulate the training environment, run the code cell under **Permission setup for invoking AWS RoboMaker from this notebook** and follow the instructions thereafter to add `robomaker.amazonaws.com` as another trusted entity of the previously created IAM role\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-trust-robomaker-in-iam-role.png)

1. To set up the required permissions for SageMaker to access the S3 storage, run the code cell under **Permission setup for SageMaker to S3 bucket** and folow the instructions thereafter to attach the **AmazonS3FullAccess** policy to the IAM role previously created\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-attach-s3fullaccess-to-iam-role.png)

1. To provision a docker container for running our training and evalution jobs, run the code cell under **Build and push docker image**\. 

     
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-provision-docker-container.png)

   Building and pushing the docker image takes some time to finish\.

1. To enable VPC mode for SageMaker and AWS RoboMaker to communicate with each other over network, run the code cell under **Configure VPC**\. By default, the notebook instance uses your default VPC, security group, and subnets to configure the VPC mode\. If you don't want open VPC for other traffic, make sure to set the **Inbound Rules** and **Outbound Rules** for the specified security group to allow incoming traffic from itself only\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-initialize-vpc-incoming-traffic.png)

1. To enable the SageMaker training job to access S3 resources, run the code cell under **Create Route Table** to create a VPC S3 endpoint\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-create-vpc-s3-endpoint.png)

At this point, you're done with initializing the training and are ready to move on to [set up the training environment](#train-evaluate-models-using-sagemaker-notebook-set-up-environment)\.

## Set Up the Training Environment<a name="train-evaluate-models-using-sagemaker-notebook-set-up-environment"></a>

Setting up the environment for training your AWS DeepRacer model involves selecting a race track, a reward function and the associated action space, as well as hyperparameters used for training\. 

The notebook uses the default settings for these\. To view the default settings, uncomment relevant parts and then run the code cell under **Configure the preset for RL algorithm**\. For example, to view the code listing of the reward function, run the code cell as follows:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebokk-view-edit-reward-function.png)

If you decide to use the default settings, copy the files to the S3 bucket\. To modify any of the files, follow the steps below, changing the file name and directory for anything other than the default reward function\.

**To modify the reward function in the *default\.py* file:**

1. Choose **File** menu on the top of the notebook instance page and then choose **Open\.\.\.**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-open-file-to-edit.png)

1. Navigate to the *src/markov/rewards* folder and choose *default\.py* to open the file\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-naviate-to-reward-function-file.png)

1. Edit the file as you see fit\. After finishing editing the file, choose **File\->Save** to save the update\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-save-reward-function-edits.png)

Notice that the environment file is shared by both SageMaker and AWS RoboMaker, also known as nodes\. When it's used by SageMaker, the `node_type` is `SAGEMAKER_TRAINING_WORKER`\. When it's used by AWS RoboMaker, the `node_type` is `SIMULATION_WORKER`\.

## Train Your AWS DeepRacer Model<a name="train-evaluate-models-using-sagemaker-notebook-train-model"></a>

Training your model with SageMaker and AWS RoboMaker amounts to executing the code in the *training\_worker\.py* file under the notebook's *src* directory\. The *training\_worker\.py* file is designated as the entry point of your training job\. 

The training process involves using AWS RoboMaker to emulate driving experiences in the environment, relaying the experiences at fixed intervals to SageMaker as input to train the deep neural network, and updating the network weights to an S3 location\. 

While the training is in progress, you can have specified training metrics logged to Amazon CloudWatch Logs or displayed to the AWS RoboMaker terminal\.

**To train your AWS DeepRacer model**

1. Run the code cell under **Copy custom files to S3 bucket so that sagemaker & robomaker can pick it up** copy the environment files to S3 \. 

     
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-copy-environment-files-to-s3.png)

1. To start an SageMaker job to train your AWS DeepRacer model, do the following:

   1. Run the first code cell under **Train the RL model using the Python SDK Script mode** to define training metrics to watch in either CloudWatch Logs or in an AWS RoboMaker console window\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-train-set-up-metrics.png)

      You can watch the specified metrics to monitor the training and to find out the effectiveness of your chosen reward function in CloudWatch Logs or using an AWS RoboMaker terminal\.

   1. Run the second code cell under **Train the RL model using the Python SDK Script mode** to start an SageMaker training job for your model\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-train-create-job.png)

      This SageMaker training job uses the TensorFlow framework and runs on a specified EC2 compute instance type\. The output lists the job name\. You can track the status of this training job in SageMaker\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-train-create-job-inprogress.png)

       

1. To create an environment simulation job in AWS RoboMaker, run the code cells under **Start the RoboMaker job** and **Create Simulation Application**\.

1. To start the simulation on AWS RoboMaker and share the simulated data, run the code cell under **Launch the Simulation job on RoboMaker**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-train-launch-simulation-job.png)

1. To watch the simulations in AWS RoboMaker, run the code cell under **Visualizing the simulations in RoboMaker** and then choose the **Simulation 1** link from the output\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-train-watch-simulation.png)

   Alternatively, you can go to the AWS RoboMaker console directly to open the simulation job\. 

   After the simulation job is initialized, the AWS RoboMaker console makes available the following visualization utilities:
   + **Gazebo**: an emulation of 3D worlds for simulating autonomous vehicle in the chosen track\.
   + **rqt**: Qt\-based framework and plugins for ROS GUI development\.
   + **ivis**: ROS visualizer for displaying the field of vision as captured by the vehicle's front\-facing camera\.
   + **Terminal**: A terminal application to provide command line access on the simulation job host\.

   1.  To view your vehicle learning in the 3D simulation, double\-click or tap **Gazebo**\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-simulation-job-gazebo.png)

      You watch the simulated vehicle navigate along the track in repeated trials starting from the starting point and ending at going off\-track or reaching the finishing line\. In the beginning, the vehicle can stay on the track briefly\. As time goes on, it learns to stay on the track longer\.

   1. To access **rqt** utilities, double\-click or tap **rqt** and choose a plugin\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-simulation-job-rqt.png)

      For more information about the plugins, see AWS RoboMaker plugins\.

   1. To view the front\-facing vision of the vehicle, double\-click or tap **rvis**\. Choose **Add** to create a visualization\. And then choose the **By topic** tab, scroll down to choose **/camera/zed/rgb/image\_rec\_color/Image**, choose OK\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-simulation-job-rvis.png)

   1. To use the terminal, double\-click or tap **Terminal** to open a terminal window on the simulation job host and type appropriate shell command\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-simulation-job-terminal.png)

      With the simulation job host terminal opened, you can call Linux shell commands to view \(`more` or `tail`\) the logs or performing other operations\. 

      To view the reward of the last 10 steps in the simulation logs, you can type the following shell command in the terminal:

      ```
      tail /tmp/simulation-logs/stdout_and_stderr
      ```

1. To visualize the training performance, run the two code cells under **Plot metrics for training job**\. When all is done successfully, you see a plot of **Training reward** vs **Episode \#** similar to the following\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/sagemaker-notebook-train-plot-metrics.png)

    In this particular example, the training reward appears to start to plateau\. Perhaps more data are needed to verify if it's true\. If the training job is running, you can run the code cell under **Plot metrics for training job** again to include more recent data into the plot\. If they persist, the onset of large fluctuations can indicate certain deficiency in the reward function\. Thus, you might update the reward function definition\. In any case, you need to collect more data with more training\.

   After training has elapsed the specified amount of time, you can locate the trained model artifacts in the training job's S3 bucket, e\.g\., *s3://*<bucket>*/*<sagemaker\-training\-job\-name>*/output/model\.tar\.gz*\. Download the model artifacts file, copy it to a USB drive and then transfer the file to your AWS DeepRacer vehicle's compute module\. 
   + To clean up when you're done with training and no longer need the AWS RoboMaker and SageMaker resources, run the two code cells under **Clean Up**\.
   + To evaluate the model that has been trained thus far, run the code cell under **Evaluation**\. 

     If successful, a simulation job is created for the task in AWS RoboMaker\. Make note of the job name in the output below the code cell\. You may need it to open the simulation job in the AWS RoboMaker console\. This simulation job is similar to the simulation job for training\. It provides the same utilities for you view the evaluation in progress in the AWS RoboMaker console\. In particular, you can watch the evaluation trials in **Gazebo**\.
   + When you're done with evaluating the model and want to terminate the simulation application, run the code cell under **Clean Up Simulation Application Resource**\.