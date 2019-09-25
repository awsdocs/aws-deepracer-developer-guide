# Evaluate Your AWS DeepRacer Models in Simulation<a name="deepracer-get-started-test-in-simulator"></a>

 After your model is trained, use the AWS DeepRacer console to evaluate its performance\. In AWS DeepRacer, the performance metric is the time required to complete a track\. following the inferred actions as prescribed by the trained model\.

To evaluate a trained model using the AWS DeepRacer console, follow the steps below\. 

1. On your model's details page, under the **Evaluation** section, choose **Start evaluation**\. 

   You can start an evaluation after your model is in a **Ready** state\. A model is ready when the training is complete\. If the training is not complete, the model might also be in a ready state if its trained up to the failing point\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-training-completed.png)

1. Under **Select environment to start evaluation**, choose an evaluation track\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-evaluate-select-track.png)

   Typically, you want to choose a track that is the same as or similar to the one you used in [training the model](deepracer-get-started-training-model.md#deepracer-get-started-train-model-proc)\. You can choose any track for evaluating your model, however, you can expect the best performance on a track most similar to the one used in training\.

1.  To specify the stop condition, leave the default value \(`3 trials`\) as\-is for **Number of trials**\. You can specify 3\-5 trial runs for each evaluation\.

1.  Choose **Start evaluation** to start creating and initializing the evaluation job\. 

   This initialization process takes about 3 minutes to complete\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-evaluation-initializing.png)

1. After evaluation is in progress, choose **Stop evaluation** if you would like to stop the evaluation for any reason\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-evaluation-in-progress.png)

    To stop an evaluation job, choose **Stop evaluation** on the upper\-right corner of the **Evaluation** pane and then confirm to stop the evaluation\. 

1. After evaluation completed successfully, inspect the **Evaluation results** to see how your model performs\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-get-started-evaluation-completed.png)

   The **Time** values listed under **Evaluation results** show how fast a trial lasts from the start position to the finish line or getting off\-track\. The **Trial results \(% completed\)** value shows the percentage of the track that was completed\. A `100%` value means the trial completed successfully\. 

   Anything less than 100 percent means the trial failed\. A model with a less than 100 percent trial result is not ready for racing\. You can anticipate such failure when the [total reward](deepracer-console-train-evaluate-models.md#deepracer-train-models-define-reward-function) in the training doesn't appear to have converged\. In this case, you can continue to improve the model by cloning it, changing the reward function, tuning hyperparameters, and then iterating the process until the total reward converges and the performance metrics improve\. For more information on how to improve the training, see [Train and Evaluate AWS DeepRacer Models](create-deepracer-project.md)\. 

 

 To transfer your completely trained model to your AWS DeepRacer vehicle for driving in a physical environment, you need to first download the model artifacts\. To do so, choose **Download model** on the model's details page\. For more information about testing an AWS DeepRacer model with a physical agent, see [Operate Your AWS DeepRacer Vehicle ](operate-deepracer-vehicle.md)\.

If you've trained your model on a track identical or similar to the one chosen in a racing event of the AWS DeepRacer League, you can submit the model to the event\. Do this by choosing **DeepRacer League** from the primary navigation pane on the AWS DeepRacer console\. For more information, see [Rank AWS DeepRacer Models in Leaderboard](deepracer-racing-series.md)\.