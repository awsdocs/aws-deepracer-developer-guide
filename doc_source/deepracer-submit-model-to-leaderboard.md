# Join an AWS DeepRacer League Virtual Circuit Race<a name="deepracer-submit-model-to-leaderboard"></a>

 In this section, learn how to use the AWS DeepRacer console to submit your trained model to a Virtual Circuit race\. 

**To enter in the AWS DeepRacer League Virtual Circuit**

1. Sign in to the AWS DeepRacer console at [https://console\.aws\.amazon\.com/deepracer](https://console.aws.amazon.com/deepracer)\.

1. From the main navigation pane, choose **AWS Virtual Circuit**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-choose-virtual-circuit.png)

1. On the **AWS Virtual Circuit** page, select a race type, and then choose **Enter race\.**  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-choose-a-race.png)

1. If this is your first time participating in an AWS DeepRacer League racing event, set your alias in **Racer name** under **AWS DeepRacer League racer name**\. You can't change your racing alias after you create it\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-create-your-alias-in-league.png)

1. Under **Model submission details**, choose your model from the **Model** list\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-submit-model.png)

1. If this is your first time participating in an AWS DeepRacer League event, under **User terms and services**, select the **I have read and agree to the terms and conditions of the DeepRacer League** check box\. 

   Follow the link to read the terms and conditions before selecting this option\.

1. Choose **Submit model** to complete the submission\.

   After your model is submitted, the AWS DeepRacer console starts its evaluation\. The process can take up to 10 minutes\.

1. On the race page, inspect the race track to ensure that your model has been trained to handle the track shape\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-track-of-race.png)

1. On the race page, view your submission status under your racer name\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-race-ranking-details.png)

1. On the race page, inspect the ranking list on the leaderboard to see how your model compares with others\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-leaderboard-ranks.png)

   If your model can't finish the track in three consecutive trials, it is not included in the ranking list on the leaderboard\. If a subsequent submission yields a faster result, your model's ranking is updated to reflect your best performance at the time\.