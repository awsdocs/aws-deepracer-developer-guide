# Join an AWS DeepRacer Virtual Circuit Race<a name="deepracer-submit-model-to-leaderboard"></a>

 In this section, you learn the steps to use the AWS DeepRacer console to submit your trained model to a virtual race in Virtual Circuit \. 

**To enter in the AWS DeepRacer League Virtual Circuit**

1. Sign in to the AWS DeepRacer console at [https://console\.aws\.amazon\.com/deepracer](https://console.aws.amazon.com/deepracer)\.

1. From the main navigation pane, choose **Official DeepRacer Virtual Circuit**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-choose-virtual-circuit.png)

1. On the **DeepRacer Virtual Circuit** page, choose an open race, and then choose **Submit model\.**  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-choose-a-race.png)

1. If this is your first time participating in an AWS DeepRacer League racing event, set your alias in **Racer name** under **AWS DeepRacer League alias**\. You can't change your racing alias after you create it\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-create-your-alias-in-league.png)

1. Under **Model submission details**, choose your model from the **Model** list\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-submit-model.png)

1. If this is your first time participating in a AWS DeepRacer event, under **User terms and services**, select the **I have read and agree to the terms and conditions of the DeepRacer League** check box\. 

   Follow the link to read the terms and conditions before selecting this option\.

1. Choose **Submit model** to complete the submission\.

   After your model is submitted, the AWS DeepRacer console starts its evaluation\. The process can take up to 10 minutes to be confirmed\.

1. On the racing event page, inspect the race track to ensure that your model has been trained to handle the track shape\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-track-of-race.png)

1. On the racing event page, inspect submission status under your alias\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-race-ranking-details.png)

1. On the racing event page, inspect the ranking list under **Leaderboard** to see how your model compares with others\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-leaderboard-ranks.png)

   If your model can't finish the track in specified three consecutive trials, it is not included in the ranking list under **Leadboard**\. If a subsequent submission yields a faster result, your model's ranking is updated to reflect your best performance at the time\.