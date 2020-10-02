# Organize an AWS DeepRacer Community Race<a name="deepracer-create-community-race"></a>

*Community races* are races organized by AWS DeepRacer users who are not officially sponsored by AWS\.

You can create your own community race and invite your colleagues, classmates, or friends by sharing a race invitation link\.

## Create a Community Race<a name="community-race-presets"></a>

You can set up a race quickly using the default community race settings\.

**To create an AWS DeepRacer community race**

1. Open the [AWS DeepRacer console](https://console.aws.amazon.com/deepracer)\.

1. Choose **Community races**\.

1. On the **Community races** page, choose **Create race**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-community-race-create.png)

1. On the **Race Details** page, choose a race type\. Race types increase in complexity from **Time trial** to **Object avoidance** to **Head\-to\-bot**\. For first time racers, we recommend **Time trial**\. Time trial races require only one camera, so the sensor configuration is simpler, and reinforcement learning \(RL\) models trained for this type of race converge faster\. For more information about race types, see [Tailor AWS DeepRacer Training for Time Trials, Object Avoidance, and Head\-to\-Bot Races](deepracer-choose-race-type.md#deepracer-get-started-training-simple-time-trial)\.

1. Enter an original, descriptive name for the race\.

1. Specify the starting and closing dates of the event in 24\-hour format\. The AWS DeepRacer console automatically recognizes your time zone\.

1. To use the default race settings, choose **Next**\.

1. On the **Review race details** page, check the race specifications\. To make changes, choose **Edit** or **Previous** to return to the **Race details** page \. When you're ready to get the invitation link, choose **Submit**\.

1. To share your race, choose **Copy invitation link** and paste it into emails, text messages, and your favourite social media applications\. All races are private and can be seen only by racers with the invitation link\. The link expires on the race's close date\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-community-race-done.png)

1. Choose **Done**\. The **Manage races** page is displayed\.

To change the race track selected, add a race description, pick a ranking method, decide how many resets racers are allowed, determine the minimum number of laps an RL model must complete to qualify for your race, set the off\-track penalty, and customize other race details, choose **Edit race details** in [Manage Community Races](deepracer-manage-community-races.md)\.

## Customize Your AWS DeepRacer Community Race<a name="customize-community-race"></a>

To customize your race, change the default community race settings\. The settings for a time trial race also apply to object avoidance and head\-to\-bot races, but object avoidance and head\-to\-bot race types have unique settings that give you the control to tailor each race environment to your event goals\.

**To customize a race**

1. Choose a competition track\. You can sort tracks by **Popularity: Most to least/Least to most**, **Difficulty: Most to least/Least to most**, and **Length: Longest to shortest/shortest to longest**\. To see all tracks in each category, choose **View more race track options**\. To close the expanded menu, choose **View fewer race track options**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-community-race-details.png)

1. For **Description**, enter a description for the event that clearly summarizes its goals and rules for participants\.

1. For **Ranking method**, choose between the **Best lap time**, where the winner is the racer who posts the fastest lap, or **Total time**, where the winner is the racer with the fastest overall average\.

1. For **Resets**, choose the maximum number of times each racer can rerun the race\. A high number of resets is helpful for inexperienced racers\.

1. For **Minimum laps**, choose the number of consecutive laps a racer must complete to qualify for submission of the result to the race's leaderboard\. For a beginners' race, choose a smaller number\. For advanced users, choose a larger number\.

1. For **Off\-track penalty**, choose the number of seconds to add to a racer's time when their RL model drives off track\.

1. You have now completed all the customization options for a **Time trial** race\. If you chose a **Time trial** race format, choose **Next** to review race details\. If you chose an [Object Avoidance](#object-avoidance-customizations) or [Head\-to\-bot](#head-to-bot-customizations) race format, skip to the appropriate procedure to finish customizing your race\.

1. On the **Review race details** page, review the race specifications\. To make changes, choose **Edit** or **Previous** to return to the **Race details** page\. When you're ready to get the invitation link, choose **Submit**\.

1. To share your race, choose **Copy invitation link** to your clipboard and paste it into emails, text messages, and your favourite social media applications\. All races are private and can be seen only by racers with the invitation link\. The link expires on the race's close date\.

1. Choose **Done**\. The **Manage races** page is displayed\.

To learn about what you can do with your race, see [Manage Community Races](deepracer-manage-community-races.md)\.<a name="object-avoidance-customizations"></a>

**To finish customizing an object avoidance race**

1. For **Collision penalty**, choose the number of seconds added to a racer's time for colliding with an object or bot\. Larger numbers intensify the challenge\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-community-race-custom-objects.png)

1. For **Number of objects**, choose how many obstacles a racer must avoid on the track\. The more objects, the more difficult the race\.

1. To add random objects to the race track for a more challenging race, choose **Include random objects** \. It takes more time and trial and error to train RL models that generalize well to random events like unexpected objects on a race track\.

1. Choose where to place each object by choosing a lane number or object location for **Lane placement**\. The track is divided in half at the center line, creating inside and outside lanes\. You can place an object on either the inside or outside lane\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-community-race-objects.png)

1. For each object, choose a value for **Location \(%\) between start and finish**\. The number represents the location, represented as a percentage, between the starting and finish lines of your track where you want to place the object\.

1. You have now completed all the unique customization options for an object avoidance race\. Choose **Next**\.

1. On the **Review race details** page, review the race specifications\. To make changes, choose **Edit** or **Previous** to return to the **Race details** page\. When you're ready to get the invitation link, choose **Submit**\.

1. To share your race, choose **Copy invitation link** and paste it into emails, text messages, and your favourite social media applications\. All races are private and can be seen only by racers with the invitation link\. The link expires on the race's close date\.

1. Choose **Done**\. The **Manage races** page is displayed\.

To learn about what you can do with your race, see [Manage Community Races](deepracer-manage-community-races.md)\.<a name="head-to-bot-customizations"></a>

**To finish customizing a head\-to\-bot race**

1. For **Number of bot cars**, choose the number of cars you want to race against your participants' AWS DeepRacer RL models\. Bot cars are similar to video game AI vehicles\. They are random objects that move, so they are a step up in complexity from stationary objects\. The more bots on the track, the more challenging the race\. Choose up to six\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-community-race-custom-bots.png)

1. For **Bot car speed**, choose how fast you want the bot cars to move around the track\. Speed is measured in meters per second\. The speed must be between 0\.2\-6 meters per second\.

1. If you want to allow bots to change lanes, which adds further complexity to the challenge for your racers' AWS DeepRacer RL models, choose **Enable lane change**\.

1. For **Minimum lane change time** , choose the minimum number of seconds that pass between instances where the bot cars change lanes\.

1. For **Maximum lane change time**, choose the maximum number of seconds that pass between instances where the bot cars change lanes\.

1. You have now completed all the unique customization options for a head\-to\-bot race\. Choose **Next**\.

1. On the **Review race details** page, review the race specifications\. To make changes, choose **Edit** or **Previous** to return to the **Race details** page\. When you're ready to get the invitation link, choose **Submit**\.

1. To share your race, choose **Copy invitation link** and paste it into emails, text messages, and your favourite social media applications\. All races are private and can be seen only by racers with the invitation link\. The link expires on the race's close date\.

1. Choose **Done**\. The **Manage races** page is displayed\.

To learn about what you can do with your race, see [Manage Community Races](deepracer-manage-community-races.md)\.