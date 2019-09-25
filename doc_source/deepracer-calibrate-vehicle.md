# Calibrate Your AWS DeepRacer Vehicle<a name="deepracer-calibrate-vehicle"></a>

To achieve the best performance, it's essential that you calibrate some physical parts of your AWS DeepRacer vehicle\. If you use an uncalibrated vehicle, it can add uncertainty when testing your model\. If the vehicle's performance is not optimal, you might be tempted to only adjust the deep learning model code\. However, you won't be able to improve the vehicle performance if the root cause is mechanical\. Adjust the mechanics by calibration\.

To calibrate your AWS DeepRacer vehicle, set the [duty cycle](https://en.wikipedia.org/wiki/Duty_cycle) range for the vehicle's electronic control system \(ECS\) and its servomechanism \(servo\), respectively\. Both the servo and ECS accept [pulse\-width modulation \(PWM\)](https://en.wikipedia.org/wiki/Pulse-width_modulation)\) signals as control input from the vehicle's compute module\. The compute module adjusts both of the vehicle's speed and steering angle by changing the duty cycles of the PWM signals\. 

The maximum speed and steering angle defines the span of the action space\. You can specify the maximum speed and maximum steering angle during training in simulation\. When deploying the trained model to your AWS DeepRacer vehicle for driving on a real\-world track, the maximum speed and steering angle of the vehicle must be calibrated to match those used in the simulation training\.  

To ensure that the real\-world experiences match the simulated experiences, you should calibrate your vehicle to match the maximum speed and maximum steering angles between the simulation and the real world\. In general, there are two ways to do this calibration:
+ Define the action space in training and calibrate the physical vehicle to match the settings\.
+ Measure the actual performance of your vehicle and change the settings of the action space in the simulation\.

A robust model can handle certain differences between the simulation and the real world\. However, you should experiment with either approach and iterate to find the best results\.

Before starting the calibration, turn on the compute module\. After it's started and the power LED has turned solid blue, turn on the vehicle battery\. After you hear two short beeps and one long beep, you're ready to proceed with the calibration\. 

**To calibrate your AWS DeepRacer vehicle to match the training settings:**

1. Follow [these instructions](deepracer-set-up-vehicle-test-drive.md) to access your vehicle and open the device control console\.

1. Choose **Calibration** from the main navigation pane\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-choose.png)

1. On the **Calibration** page, choose **Calibrate** in **Steering** and then follow the steps below to calibrate the vehicle's maximum steering angles\.

   1. Set the vehicle on the ground or another hard surface where you can see the wheels during the steering calibration\. Choose **Next**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-steering-place-on-ground.png)

      Steering a vehicle on a track requires the much smaller steering angles than turning wheels in the air\. To measure the actual steering angles of the wheels, it's important that you place the vehicle down on the track surface\.

   1. Under **Center steering**, gradually move the slider or press the left or right arrow to the position where at least one of the front wheels is aligned with the rear wheel on the same side\. Choose **Next**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-steering-center.png)

      AWS DeepRacer uses [Ackermann front\-wheel steering](https://en.wikipedia.org/wiki/Ackermann_steering_geometry) to turn wheels on the inside and outside of a turn\. This mean that the left and right front wheels generally turn at different angles\. In AWS DeepRacer, the calibration is done on the center value\. Therefore, you need to adjust the wheels on the selected side to be aligned in a straight line\.
**Note**  
Make sure to [calibrate your AWS DeepRacer vehicle well](#deepracer-calibrate-vehicle) so that it can maintain center steering as straight as possible\. You can test this by manually pushing the vehicle to verify it follows a straight path\.

   1. Under **Maximum left steering**, gradually move the slider to the left or press the left arrow until the vehicle front wheels stops turning left\. There will be a quiet noise\. If you hear a loud noise, you have gone too far\. The position corresponds to the maximum left steering angle\. If you have limited your steering angle in the simulated action space, match the corresponding value here\. Choose **Next**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-steering-left.png)

      To measure the actual maximum left steering angle, draw a center line for the vehicle, mark the two edge points of the selected front wheel for calibration, and draw the center line of this front wheel until it crosses over the center line of the vehicle\. Use a protractor to measure the angle\. See the figure below\. If you want to match the actual angle in your training, you can set the same value in the action space in your next training job\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-measure-steering-angle.png)

   1. Under **Maximum right steering**, gradually move the slider to the right until the selected front wheels stop turning right\. There will be a quiet noise\. If you hear a loud noise, you have gone too far\. The position corresponds to the maximum right steering angle\. If you have limited your steering angle in the simulated action space, match the corresponding value here\. Choose **Done**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-steering-right.png)

   To measure the actual maximum right steering angle, follow the steps similar to those used to measure the maximum left steering angle\. 

   This concludes the steering calibration for your AWS DeepRacer vehicle\. 

1. To calibrate the vehicle's maximum speed, choose **Calibrate** in **Speed** on the **Calibration** page and then follow the steps below\.

   1. Raise the vehicle so that the wheels are free to turn\. Choose **Next** on the device control console\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-throttle-raise-vehicle.png)
**Note**  
If the vehicle's speed has been set too high, it may run too fast during calibration and cause damage to the environment, the vehicle, or others nearby\. You should raise the vehicle, as instructed here, but not hold it in your hands\.

   1. To calibrate the stopped speed, press the left or right arrow to gradually change **Stopped value** under **Stopped speed** on the device control console until the wheels stop turning\. Choose **Next**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-throttle-stopped.png)
**Note**  
When pressing the **Stopped value** further left or further right to the value when you start hearing noises, the wheels are about to move\. The ideal zero\-throttle point is the middle of the two values\. For example, if you start hearing a noise at 16 on the left and at \-4 on the right, the optimal stopped value should be 10\.

   1. To set the vehicle's forward direction, place the vehicle as shown on the screen and the image here, and then press the left or right arrow to make the wheels turn\. If the wheels turn clock\-wise, the forward direction is set\. If not, toggle **Reverse direction**\. Choose **Next**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-throttle-polarity.png)
**Note**  
Vehicles distributed at AWS re:Invent 2018 might have their forward direction set in reverse\. In such a case, make sure to toggle **Reverse direction**\.

   1. To calibrate the maximum forward speed, under **Maximum forward speed**, gently move the slider left or right to adjust the **Maximum forward speed value** number gradually to such a positive value that the **Estimated speed** value is equal or similar to the maximum speed specified in the simulation\. Choose **Next**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-throttle-maximum-forward.png)
**Note**  
The actual maximum speed your vehicle depends on the friction of the track surface as well as the vehicle battery level\. To make it flexible, you can set the vehicle's throttle limit to be 20\-30 percent higher than the maximum speed specified for training in the simulation\. Generally speaking, you should set the maximum speed value within the green area\. Above that, your vehicle is likely to drive too fast at increased risk of breaking\. Additionally, the action space for training doesn't support the maximum speed of more than 2 m/s\. 

   1. To calibrate the maximum backward speed, under **Maximum backward speed**, gently move the slider left or right to adjust the **Maximum backward speed value** number gradually to such a negative value that the **Estimated speed** value is equal or similar to the maximum speed specified in the simulation\. Choose **Done**\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-calibration-throttle-maximum-reverse.png)
**Note**  
The AWS DeepRacer vehicle doesn't use backward speed in the autonomous driving mode\. You can set the backward speed to any value with which you can comfortably control the vehicle's manual driving mode\. 

   This concludes calibrating your AWS DeepRacer vehicle's maximum speed\.