# Submit Your Model to an AWS DeepRacer Leaderboard<a name="deepracer-submit-model-to-leaderboard"></a>

 In this section, you can see the steps to use the AWS DeepRacer console to submit your trained model to a virtual race\. 

**To submit your model to a virtual leaderboard in the Virtual circuit**

1. Sign in to the AWS DeepRacer console at [https://console\.aws\.amazon\.com/deepracer](https://console.aws.amazon.com/deepracer)\.

1. From the main navigation pane, choose **DeepRacer Virtual Circuit**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-choose-virtual-circuit.png)

1. On the **DeepRacer Virtual Circuit** page, choose an open race, and then choose **Submit model\.**  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-choose-a-race.png)

1. If this is your first time participating in an AWS DeepRacer League racing event, set your alias in **Racer name** under **AWS DeepRacer League alias**\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-create-your-alias-in-league.png)

1. Under **Model submission details**, choose your model from the **Model** drop\-down menu\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-submit-model.png)

1. If this is your first time participating in a DeepRacer League event, under **User terms and services**, check the **I have read and agree to the terms and conditions of the DeepRacer League** option\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-accept-terms-of-agreement.png)

   Follow the link to read the terms and conditions before checking this option\.

1. Choose **Submit model** to complete the submission\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-start-submit-model.png)

   After yoru model is submitted, AWS DeepRacer starts to evaluate it\. The process takes some time\.

1. On the racing event page, inspect the race track to ensure that your model has been trained to handle the track shape\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-track-of-race.png)

1. On the racing event page, inspect submission status under your alias\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-race-ranking-details.png)

1. On the racing event page, inspect the ranking list under **Leaderboard** to see how your model compares with others\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-leaderboard-ranks.png)

   If your model cannot finish the track in specified three consecutive trials, it is not included in the ranking list under **Leadboard**\. If a subsequent submission yields a faster result, your model's ranking is updated to reflect your best performance at the time\.