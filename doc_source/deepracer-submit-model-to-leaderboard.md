# Join an AWS DeepRacer League Virtual Circuit Race<a name="deepracer-submit-model-to-leaderboard"></a>

 In this section, learn how to use the AWS DeepRacer console to submit your trained model to a Virtual Circuit race\. 

**To enter in the AWS DeepRacer League Virtual Circuit**

1. Sign in to the AWS DeepRacer console at [https://console\.aws\.amazon\.com/deepracer](https://console.aws.amazon.com/deepracer)\.

1. From the main navigation pane, choose **AWS Virtual Circuit**\.

1. On the **AWS Virtual Circuit** page, find the race in your division that you'd like to enter, and choose **Enter race**\. 
   + All racers begin in the Open Division\. Open Division racers compete in the time trial format and receive monthly digital rewards for participation\. Racers who earn a top 10% result on the leaderboard move on to the Pro Division\. 
   + Pro Division racers compete in the more complex head\-to\-head and object avoidance racing formats, which require stereo camera or LiDAR sensor configurations\. Pros also earn bigger rewards and can enter the monthly finale for a chance to win qualifying seats in the yearly AWS re:Invent Championship Cup\.
   + As an Open Division Racer, you can enter Open Division Races and view Pro Division Leaderboards, but not enter Pro Division races\. \(Optional\) Add the Pro Division Finale to your calendar as a reminder to watch it live\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-virtual-circuit-open-race-card.png)
   + As a Pro Division racer, you can enter Pro Division Races and the monthly Pro Division Finale\. Once you are Pro, you can view Open Division Leaderboards, but not enter Open Division races\. \(Optional\) Add the Pro Division Finale to your calendar as a reminder to participate or spectate\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-virtual-circuit-pro-race-card.png)

1. If this is your first time participating in an AWS DeepRacer League racing event, set your alias in **Racer name** under **AWS DeepRacer League racer name**\. You can't change your racing alias after you create it\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-create-your-alias-in-league.png)

1. Under **Choose model**, select the model you'd like to use from the **Model** list\. Ensure that your model has been trained to handle the track shape\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-submit-model.png)

1. If this is your first time participating in an AWS DeepRacer League event, under **User terms and services**, follow the link to read the terms and conditions\. Then, if you agree, select the **I have read and agree to the terms and conditions of the DeepRacer League** check box\.

1. Choose **Submit model** to complete the entry\.

   After your model is submitted, the AWS DeepRacer console starts its evaluation\. The process can take up to 10 minutes\.

1. On the race page, review the race details\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-virtual-circuit-competition-track.png)

1. On the race page, note your submission status under your racer name\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-race-ranking-details.png)

1. On the race page, view the ranking list on the leaderboard to see how your model compares with others\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-league-leaderboard-ranks.png)

   If your model doesn't finish the track in three consecutive trials, it is not included in the ranking list on the leaderboard\. There is no limit to the number of submissions you can make while the race is open\. Your leaderboard ranking reflects your best performing submission\.

   After you submit a model, try improving its performance by refining your reward function\. You can also train a new model with a different algorithm or action space\. Learn, adjust, and race again to increase your chances for rewards\.