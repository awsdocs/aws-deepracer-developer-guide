# Evaluate Your AWS DeepRacer Models in Simulation<a name="deepracer-get-started-test-in-simulator"></a>

 After your training job is complete, you should evaluate the trained model to assess its convergency behavior\. The evaluation proceeds by completing a number of trials on a chosen track and having the agent move on the track according to likely actions inferred by the trained model\. The performance metrics include a percentage of track completion and the time running on each track from start to finish or going off\-track\. 

To evaluate your trained model, you can use the AWS DeepRacer console\. To do so, follow the steps in this topic\. 

**To evaluate a trained model in the AWS DeepRacer console**

1. Open the AWS DeepRacer console at https://console\.aws\.amazon\.com/deepracer\. 

1. From the main navigation pane, choose **Models** and then choose the model you just trained from the **Models** list to open the model details page\.

1. In **Evaluation**, choose **Start evaluation**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-evaluation-start.png)

   You can start an evaluation after your training job status changes to **Completed** or the model's status changes to **Ready** if the training job wasn't completed\. 

   A model is ready when the training job is complete\. If the training wasn't completed, the model can also be in a **Ready** state if it's trained up to the failing point\.

1. On the **Evaluate model** page, under **Evaluate criteria**, choose a track under **Evaluation criteria**\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-evaluate-select-track.png)

   Typically, you want to choose a track that is the same as or similar to the one you used in [training the model](deepracer-get-started-training-model.md#deepracer-get-started-train-model-proc)\. You can choose any track for evaluating your model, however, you can expect the best performance on a track most similar to the one used in training\. 

   To see if your model generalizes well, choose an evaluation track different from the one used in training\. 

1. On the **Evaluate model** page, under **Evaluate criteria**, choose the number of trials you want to use to evaluate the model\. 

1. On the **Evaluate model** page, under **Race type**, choose the racing type that you chose to train the model\. 

   For evaluation you can choose a race type different from the race type used in training\. For example, you can train a model for head\-to\-head races and then evaluate it for time trials\. In general, the model must generalize well if the training race type differs from the evaluation race type\. For your first run, you should use the same race type for both evaluation and training\. 

1. On the **Evaluate model** page, under **Virtual Race Submission**, for your first model, turn off the **Submit model after evaluation** option\. Later, if you want to participate in a racing event, leave this option enabled\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-evaluate-virtual-race-submit.png)

1. On the **Evaluate model** page, choose **Start evaluation** to start creating and initializing the evaluation job\. 

   This initialization process takes about 3 minutes to complete\. 

1. As the evaluation progresses, the evaluation results, including the trial time and track completion rate, are displayed under **Evaluation** after each trial\. In the **Simulation video stream** window, you can watch how the agent performs on the chosen track\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-evaluation-in-progress.png)

    You can stop an evaluation job before it completes\. To stop the evaluation job, choose **Stop evaluation** on the upper\-right corner of the **Evaluation** card and then confirm to stop the evaluation\. 

1. After the evaluation job is complete, examine the performance metrics of all the trials under **Evaluation results**\. The accompanying simulation video stream is no longer available\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-evaluation-completed.png)

   For this particular evaluation job, the trained model fails to complete any trial\. As the first run, this is not unusual\. Possible reasons include that the training didn't converge and the training needs more time, the action space needs to be enlarged to give the agent more room to react, or the reward function needs to be updated to handle varying environments\. 

   You can continue to improve the model by cloning a previously trained one, modifying the reward function, tuning hyperparameters, and then iterating the process until the total reward converges and the performance metrics improve\. For more information on how to improve the training, see [Train and Evaluate AWS DeepRacer Models](create-deepracer-project.md)\. 

 To transfer your completely trained model to your AWS DeepRacer vehicle for driving in a physical environment, you need to download the model artifacts\. To do so, choose **Download model** on the model's details page\. If your AWS DeepRacer physical vehicle doesn't support new sensors and your model has been trained with the new sensor types, you'll get an error message when you use the model on your AWS DeepRacer vehicle in a real\-world environment\. For more information about testing an AWS DeepRacer model with a physical agent, see [Operate Your AWS DeepRacer Vehicle ](operate-deepracer-vehicle.md)\.

If you've trained your model on a track identical or similar to the one specified in an AWS DeepRacer League racing event or an AWS DeepRacer community race, you can submit the model to the virtual races in the AWS DeepRacer console\. To do this, follow **Official DeepRacer virtual circuit** or **Community races** on the main navigation pane\. For more information, see [Participate in AWS DeepRacer Virtual Races](deepracer-racing-series.md)\. 

To train a model for obstacle avoidance or head\-to\-head racing, you may need to add new sensors to the agent and the physical vehicle\. For more information, see [Understanding Racing Types and Enabling Sensors Supported by AWS DeepRacer](deepracer-choose-race-type.md)\.