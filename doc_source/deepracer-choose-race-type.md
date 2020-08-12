# Understanding Racing Types and Enabling Sensors Supported by AWS DeepRacer<a name="deepracer-choose-race-type"></a>

In AWS DeepRacer League, you can participate in the following types of racing events: 
+ **Time trial**: race against the clock on an unobstructed track and aim to get the fastest lap time possible\.
+ **Object avoidance**: race against the clock on a track with stationary obstacles and aim to get the fastest lap time possible\.
+ **Head\-to\-head racing**: race against one or more other vehicles on the same track and aim to cross the finish line before other vehicles\.

AWS DeepRacer community races currently supports time trials only\. 

You should experiment with different sensors on your AWS DeepRacer vehicle to provide it with sufficient capabilities to observe its surroundings for a given race type\. The next section describes the [AWS DeepRacer\-supported sensors](#deepracer-how-it-works-autonomous-driving-sensors) that can enable the supported types of autonomous racing events\.

**Topics**
+ [Choose Sensors for AWS DeepRacer Racing Types](#deepracer-how-it-works-autonomous-driving-sensors)
+ [Configure Agent for Training AWS DeepRacer Models](#deepracer-configure-agent)
+ [Tailor AWS DeepRacer Training for Time Trials](#deepracer-get-started-training-simple-time-trial)
+ [Tailor AWS DeepRacer Training for Object Avoidance Races](#deepracer-get-started-training-object-avoidance)
+ [Tailor AWS DeepRacer Training for Head\-to\-Head Races](#deepracer-get-started-training-h2h-racing)

## Choose Sensors for AWS DeepRacer Racing Types<a name="deepracer-how-it-works-autonomous-driving-sensors"></a>

Your AWS DeepRacer vehicle comes with a front\-facing monocular camera as the default sensor\. You can add another front\-facing monocular camera to make front\-facing stereo cameras or to supplement either the monocular camera or stereo cameras with a LiDAR unit\. 

The following list summarizes the functional capabilities of AWS DeepRacer\-supported sensors, together with brief cost\-and\-benefit analyses:

**Front\-facing camera**  <a name="term-deepracer-sensor-front-facing-monocular-camera"></a>
 A single\-lens front\-facing camera can capture images of the environment in front of the host vehicle, including track borders and shapes\. It's the least expensive sensor and is suitable to handle simpler autonomous driving tasks, such as obstacle\-free time trials on well\-marked tracks\. With proper training, it can avoid stationary obstacles on fixed locations on the track\. However, the obstacle location information is built into the trained model and, as the result, the model is likely to be overfitted and may not generalize to other obstacle placements\. With stationary objects placed at random locations or other moving vehicles on the track, the model is unlikely to converge\.   
In the real world, the AWS DeepRacer vehicle comes with a single\-lens front\-facing camera as the default sensor\. The camera has 120\-degree wide angle lens and captures RGB images that are then converted to grey\-scale images of 160 x 120 pixels at 15 frames per second \(fps\)\. These sensor properties are preserved in the simulator to maximize the chance that the trained model transfers well from simulation to the real world\.

**Front\-facing stereo camera**  <a name="term-deepracer-sensor-front-facing-stereo-cameras"></a>
A stereo camera has two or more lenses that capture images with the same resolution and frequency\. Images from the both lens are used to determine the depth of observed objects\. The depth information from a stereo camera is valuable for the host vehicle to avoid crashing into the obstacles or other vehicles in the front, especially under more dynamic environment\. However, added depth information makes trainings to converge more slowly\.   
 On the AWS DeepRacer physical vehicle, the double\-lens stereo camera is constructed by adding another single\-lens camera and mounting each camera on the left and right sides of the vehicle\. The AWS DeepRacer software synchronizes image captures from both cameras\. The captured images are converted into greyscale, stacked, and fed into the neural network for inferencing\. The same mechanism is duplicated in the simulator in order to train the model to generalize well to a real\-world environment\.

**LiDAR sensor**  <a name="term-deepracer-sensor-rear-mount-lidar"></a>
 A LiDAR sensor uses rotating lasers to send out pulses of light outside the visible spectrum and time how long it takes each pulse to return\. The direction of and distance to the objects that a specific pulse hits are recorded as a point in a large 3D map centered around the LiDAR unit\.   
For example, LiDAR helps detect blind spots of the host vehicle to avoid collisions while the vehicle changes lanes\. By combining LiDAR with mono or stereo cameras, you enable the host vehicle to capture sufficient information to take appropriate actions\. However, a LiDAR sensor costs more compared to cameras\. The neural network must learn how to interpret the LiDAR data\. Thus, trainings will take longer to converge\.   
 On the AWS DeepRacer physical vehicle a LiDAR sensor is mounted on the rear and tilted down by 6 degrees\. It rotates at the angular velocity of 10 rotations per second and has a range of 15cm to 2m\. It can detect objects behind and beside the host vehicle as well as tall objects unobstructed by the vehicle parts in the front\. The angel and range are chosen to make the LiDAR unit less susceptible to environmental noise\.

 You can configure your AWS DeepRacer vehicle with the following combination of the supported sensors: 
+ Front\-facing single\-lens camera only\.

  This configuration is good for time trials, as well as obstacle avoidance with objects at fixed locations\.
+ Front\-facing stereo camera only\.

  This configuration is good for obstacle avoidance with objects at fixed or random loations\. 
+ Front\-facing single\-lens camera with LiDAR\.

  This configuration is good for obstacle avoidance or head\-to\-head racing\.
+ Front\-facing stereo camera with LiDAR\.

  This configuration is good for obstacle avoidance or head\-to\-head racing, but probably not most economical for time trials\.

As you add more sensors to make your AWS DeepRacer vehicle to go from time trials to object avoidance to head\-to\-head racing, the vehicle collects more data about the environment to feed into the underlying neural network in training\. This makes training more challenging because the model is required to handle increased complexities\. In the end, your tasks of learning to train models become more demanding\. 

To learn progressively, you should start training for time trials first before moving on to object avoidance and then to head\-to\-head racing\. You'll find more detailed recommendations in the next section\.

## Configure Agent for Training AWS DeepRacer Models<a name="deepracer-configure-agent"></a>

 To train a reinforcement learning model for AWS DeepRacer vehicle to race in obstacle avoidance or head\-to\-head racing, you need to configure the agent with appropriate sensors\. For simple time trials, you could use the default agent configured with a single\-lens camera\. In configuring the agent you can customize the action space and choose a neural network topology so that they work better with the selected sensors to meet the intended driving requirements\. In addition, you can change the agent's appearance for visual identification during training\.

After you configure it, the agent configuration is recorded as part of the model's metadata for training and evaluation\. For evaluation, the agent automatically retrieves the recorded configuration to use the specified sensors, action space, and neural network technology\.

This section walks you through the steps to configure an agent in the AWS DeepRacer console\. 

**To configure an AWS DeepRacer agent in the AWS DeepRacer console**

1. Sign in to the [AWS DeepRacer console](https://console.aws.amazon.com/deepracer)\.

1. On the primary navigation pane, choose **Garage**\.

1. For the first time you use **Garage**, you're presented with the **WELCOME TO THE GARAGE** dialog box\. Choose **>** or **<** browse through the introduction to various sensors supported for the AWS DeepRacer vehicle or choose **X** to close the dialog box\. You can find this introductory information on the help panel in **Garage**\.

1. On the **Garage** page, choose **Build new vehicle**\.

1.  On the **Mod your own vehicle** page, under **Mod specifications**, choose one or more sensors to try and learn the best combination that can meet your intended racing types\. 

   To train for your AWS DeepRacer vehicle time trials, choose **Camera**\. For obstacle avoidance or head\-to\-head racing, you want to use other sensor types\. To choose **Stereo camera**, make sure you have acquired an additional single\-lens camera\. AWS DeepRacer makes the stereo camera out two single\-lens cameras\. You can have either a single\-lens camera or a double\-lens stereo cameras on one vehicle\. In either case, you can add a LiDAR sensor to the agent if you just want the trained model to be able to detect and avoid blind spots in obstacle avoidance or head\-to\-head racing\. 

1. On the **Garage** page and under **Neural network topologies**, choose a supported network topology\.

   In general, a deeper neural network \(with more layers\) is more suitable for driving on more complicated tracks with sharp curves and numerous turns, for racing to avoid stationary obstacles, or for competing against other moving vehicles\. But a deeper neural network is more costly to train and the model takes longer to converge\. On the other hand, a shallower network \(with fewer layers\) costs less and takes a shorter time to train\. The trained model is capable of handling simpler track conditions or driving requirements, such as time trials on a obstacle\-free track without competitors\. 

   Specifically, AWS DeepRacer supports **3\-layer CNN** or **5\-layer CNN**\. 

1. On the **Garage** page, choose **Next** to proceed to setting up the agent's action space\.

1. On the **Action space** page, leave the default settings for your first training\. For subsequent trainings, experiment with different settings for the steering angle, top speed, and their granularities\. Then, choose **Next**\.

1. On the **Color your vehicle to stand out in the crowd** page, enter a name in **Name your DeepRacer** and then choose a color for the agent from the **Vehicle color** list\. Then, choose **Submit**\. 

1. On the **Garage** page, examine the settings of the new agent\. To make further modifications, choose **Mod vehicle** and repeat the previous steps starting at **Step 4**\. 

Now, your agent is ready for training\. 

## Tailor AWS DeepRacer Training for Time Trials<a name="deepracer-get-started-training-simple-time-trial"></a>

If this is your first time to use AWS DeepRacer, you should start with a simple time trial to become familiar with how to train AWS DeepRacer models to drive your vehicle\. This way, you get a gentler introduction to basic concepts of reward function, agent, environment, etc\. Your goal is to train a model to make the vehicle stay on the track and finish a lap as fast as possible\. You can then deploy the trained model to your AWS DeepRacer vehicle to test driving on a physical track without any additional sensors\.

To train a model for this scenario, you can choose the default agent from **Garage** on the AWS DeepRacer console\. The default agent has been configured with a single front\-facing camera, a default action space and a default neural network topology\. It is helpful to start training an AWS DeepRacer model with the default agent before moving on to more sophisticated ones\.

To train your model with the default agent, follow the recommendations below\. 

1. Start training your model with a simple track of more regular shapes and of less sharp turns\. Use the default reward function\. And train the model for 30 minutes\. After the training job is completed, evaluate your model on the same track to watch if the agent can finish a lap\.

1. Read about [the reward function parameters](deepracer-reward-function-input.md)\. Continue the training with different incentives to reward the agent to go faster\. Lengthen the training time for the next model to 1 \- 2 hours\. Compare the reward graph between the first training and this second one\. Keep experimenting until the reward graph stops improving\.

1. Read more about [action space](deepracer-how-it-works-action-space.md)\. Train the model the 3rd time by increasing the top speed \(e\.g\., 1 m/s\)\. To modify the action space, you must build in **Garage** a new agent, when you get the chance to make the modification\. When updating the top speed of your agent, be aware of that the higher the top speed, the faster the agent can complete the track in evaluation and the faster your AWS DeepRacer vehicle can finish a lap on a physical track\. However, a higher top speed often means a longer time for the training to converge because the agent is more likely to overshoot on a curve and thus get off track\. You may want to decrease granularities to give the agent more rooms to accelerate or decelerate and further tweak the reward function in other ways to help training converge faster\. After the training converges, evaluate the 3rd model to see if the lap time improves\. Keep exploring until there is no more improvement\.

1. Choose a more complicated track and repeat **Step 1** to **Step 3**\. Evaluate your model on a track that is different from the one you used to train on to see how the model can generalize to different virtual tracks [generalize to real\-world environments](deepracer-how-it-works-virtual-to-physical.md)\. 

1. \(Optional\) Experiment with different values of the [hyperparameters](deepracer-console-train-evaluate-models.md#deepracer-iteratively-adjust-hyperparameters) to improve the training process and repeat **Step 1** to **Step 3**\.

1. \(Optional\) Examine and analyze the AWS DeepRacer logs\. For sample code that you can use to analyze the logs, see [https://github\.com/aws\-samples/aws\-deepracer\-workshops/tree/master/log\-analysis](https://github.com/aws-samples/aws-deepracer-workshops/tree/master/log-analysis)\.

## Tailor AWS DeepRacer Training for Object Avoidance Races<a name="deepracer-get-started-training-object-avoidance"></a>

After you become familiar with time trials and have trained a few converged models, move on to the next more demanding challenge—obstacle avoidance\. Here, your goal is to train a model that can complete a lap as fast as possible without going off track, while avoiding crashing into the objects placed on the track\. This is obviously a harder problem for the agent to learn, and training takes longer to converge\. 

The AWS DeepRacer console supports two types of obstacle avoidance training: obstacles can be placed at fixed or random locations along the track\. With fixed locations, the obstacles remain fixed to the same place throughout the training job\. With random locations, the obstacles change their respective places at random from episode to episode\. 

It is easier for trainings to converge for location\-fixed obstacle avoidance because the system has less degrees of freedom\. However, models can overfit when the location information is built in to the trained models\. As a result, the models may be overfitted and may not generalize well\. For randomly positioned obstacle avoidance, it's harder for trainings to converge because the agent must keep learning to avoid crashing into obstacles at locations it hasn't seen before\. However, models trained with this option tend to generalize better and transfer well to the real\-world races\. To begin, have obstacles placed at fixed locations, get familiar with the behaviors, and then tackle the random locations\. 

In the AWS DeepRacer simulator, the obstacles are cuboid boxes with the same dimensions \(9\.5" \(L\) x 15\.25" \(W\) x 10/5" \(H\)\) as the AWS DeepRacer vehicle's package box\. This makes it simpler to transfer the trained model from the simulator to the real world if you place the packaging box as an obstacle on the physical track\.

To experiment with obstacle avoidance, follow the recommended practice outlined in the steps below:

1. Use the default agent or experiment with new sensors and action spaces by customizing an existing agent or building a new one\. You should limit the top speed to below 0\.8 m/s and the speed granularity to 1 or 2 levels\.

   Start training a model for around 3 hours with 2 objects at fixed locations\. Use the example reward function and train the model on the track that you will be racing on, or a track that closely resembles that track\. The **2019 Championship Cup** track is a simple track, which makes it a good choice for summit race preparation\. Evaluate the model on the same track with the same number of obstacles\. Watch how the total expected reward converges, if at all\. 

1. Read about [the reward function parameters](deepracer-reward-function-input.md)\. Experiment with variations of your reward function\. Increase the obstacle number to 4\. Train the agent to see if the training converges in the same amount of training time\. If it doesn't, tweak your reward function again, lower the top speed or reduce the number of obstacles, and the train the agent again\. Repeat experimenting until there is no more significant improvement\. 

1. Now, move on to training avoiding obstacles at random locations\. You'll need to configure the agent with additional sensors, which are available from **Garage** in the AWS DeepRacer console\. You can use a stereo camera\. Or you can combine a LiDAR unit with either a single\-lens camera or a stereo camera, but should expect a longer training time\. Set the action space with a relatively low top speed \(e\.g\. 2 m/s\) for the training to converge quicker\. For the network architecture, use a shallow neural network, which has been found sufficient for obstacle avoidance\.

1. Start training for 4 hours the new agent for obstacle avoidance with 4 randomly placed objects on an simple track\. Then evaluate your model on the same track to see if it can finish laps with randomly positioned obstacles\. If not, you may want to tweak your reward function, try different sensors and have longer training time\. As another tip, you can try cloning an existing model to continue training to leverage previously learned experience\. 

1. \(Optional\) Choose a higher top speed for the action space or have more obstacles randomly placed along the track\. Experiment with different combination of sensors and tweak the reward functions and hyperparameter values\. Experiment with the **5\-layer CNN** network topology\. Then, retrain the model to determine how they affect convergence of the training\. 

## Tailor AWS DeepRacer Training for Head\-to\-Head Races<a name="deepracer-get-started-training-h2h-racing"></a>

Having gone through training obstacle avoidance, you're now ready to tackle the next level of challenge: training models for head\-to\-head races\. Unlike the obstacle avoidance events, head\-to\-head racing has a dynamic environment with moving vehicles\. Your goal is to train models for your AWS DeepRacer vehicle to compete against other moving vehicles in order to reach the finish line first without going off track or crashing to any of other vehicles\. In the AWS DeepRacer console you can train a head\-to\-head racing model by having your agent to compete against 1\-4 bot vehicles\. Generally speaking, you should have more obstacles placed on a longer track\.

Each bot vehicle follows a predefined path at constant speed\. You can enable it to change lanes or to remains on its starting lane\. Similar to training for obstacle avoidance, you can have the bot vehicles evenly distributed across the track on both lanes\. The console limits you to have up to 4 bot vehicles on the track\. Having more competing vehicles on the track provides the learning agent with more opportunities to encounter more varied situations with the other vehicles\. This way, it learns more in one training job and the agent gets trained faster\. However, each training is likely to take longer to converge\. 

To train an agent with bot vehicles, you should set the top speed of the agent's action space higher than the \(constant\) speed of the bot vehicles so that the agent has more passing opportunities during training\. As a good starting point, you should set the agent's top speed at 0\.8 m/s and the bot vehicle's moving speed at 0\.4 m/s\. If you enable the bots to change lanes, the training becomes more challenging because the agent must learn not only how to avoid crashing into a moving vehicle in the front on the same lane but also how to avoid crashing into another moving vehicle in the front on the other lane\. You can set the bots to change lanes at random intervals\. The length of an interval is randomly selected from a range of time \(e\.g\. 1s to 5s\) that you specify before starting the training job\. This lane\-changing behavior is more similar to the real\-world head\-to\-head racing behaviors and the trained agent should generate better\. However, it takes longer to train the model to converge\. 

Follow these suggested steps to iterate your training for head\-to\-head racing: 

1. In **Garage** of the AWS DeepRacer console, build a new training agent configured with both stereo cameras and a LiDAR unit\. It is possible to train a relatively good model using only stereo camera against bot vehicles\. LiDAR helps reduce blind spots when the agent changes lanes\. Do not set the top speed too high\. A good starting point is 1 m/s\.

1. To train for head\-to\-head racing against bot vehicles, start with two bot vehicles\. Set the bot's moving speed lower than your agent’s top speed \(e\.g\. 0\.5 m/s if the agent's top speed is 1 m/s\)\. Disable the lane\-changing option, and then choose the training agent you just created\. Use one of the reward function examples or make minimally necessary modifications, and then train for 3 hours\. Use the track that you will be racing on, or a track that closely resembles that track\. The **2019 Championship Cup** track is a simple track, which makes it a good choice for summit race preparation\. After the training is complete, evaluate the trained model on the same track\. 

1. For more challenging tasks, clone your trained model for a second head\-to\-head racing model\. Proceed to either experiment with more bot vehicles or enable lane\-changing options\. Start with slow lane\-changing operations at random intervals longer than 2 seconds\. You may also want to experiment with custom reward functions\. In general, your custom reward function logic can be similar to those for obstacle avoidance, if you don't take into consideration a balance between surpassing other vehicles and staying on track\. Depends on how good your previous model is, you may need to train another 3 to 6 hours\. Evaluate your models and see how the model performs\.