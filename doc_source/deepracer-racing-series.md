# Rank AWS DeepRacer Models in Leaderboard<a name="deepracer-racing-series"></a>

After successfully tuning and evaluating your model in simulations, you may want to compare your model's performance to other user's models\. The comparison provides another measure of the fitness of your model\. To support this, you can submit your model to an AWS DeepRacer leaderboard and see your model ranked against other participant models\. 

Each AWS DeepRacer leaderboard is associated with a racing event that uses a specific track\. The leaderboard manages a list of performance rank for user\-submitted AWS DeepRacer models and contains user aliases and average lap times of the included models\. The performance of a model is ranked according to the average lap time over a number of consecutive successful trials\. Each leaderboard can specify between three and five consecutive laps for performance ranking\. If a model evaluation does not result in the specified number of consecutive successful trials, the model is not included in the leaderboard\. 

There are two types of racing events in AWS DeepRacer League\. One is the DeepRacer League Virtual circuit and the other the DeepRacer League Summit circuit\. The Virtual circuit consists of a series of virtual races\. In a virtual race, you compete against other participants on a virtual track and qualified results are ranked in the associated virtual leaderboard\. The Summit circuit consists of a series of live, real\-time racing events\. In a live race, you compete against other participants in person on a physical track\. Qualified results are ranked in the associated physical leaderboard\. 

You can use the AWS DeepRacer console to enter a virtual race and submit a trained model for timed trials in the simulator\.This is how your qualified results get ranked in the virtual leaderboard\. New virtual racing events are opened as old ones close\. For physical races, you must enter in person and start your AWS DeepRacer vehicle for autonomous driving on the physical track\. The qualified result is posted to the associated leaderboard through the vehicle's Wi\-Fi connection\. A physical race leaderboard is typically provided by a third\-party vendor\. For example, [GoSquared](https://engineering.gosquared.com/building-the-deepracer-leaderboard) provided the physical leaderboard for the *AWS re:Invent 2018* racing event\. Currently, all AWS DeepRacer leaderboards are public and open to any AWS DeepRacer user\.

In this section, we discuss AWS DeepRacer virtual leaderboards exclusively\. 

  **

**Topics**
+ [Submit Your Model to an AWS DeepRacer Leaderboard](deepracer-submit-model-to-leaderboard.md)