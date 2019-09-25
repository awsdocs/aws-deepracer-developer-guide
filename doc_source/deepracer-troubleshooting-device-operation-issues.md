# How to Diagnose and Resolve Common AWS DeepRacer Operational Issues?<a name="deepracer-troubleshooting-device-operation-issues"></a>

As you explore reinforcement learning with your AWS DeepRacer vehicle, the device may become non functional\. The troubleshooting topics below help you diagnose the problems and resolve the issues\. 

**Topics**
+ [Why Does the Video Player on the Device Console Not Show Video Stream from My Vehicle's Camera?](#deepracer-device-why-no-video-showing-on-device-console)
+ [Why Does My AWS DeepRacer Vehicle Not Move?](#deepracer-device-why-vehicle-not-moving)
+ [Why Do I Not See the Latest Device Update and How I Get the Latest Update?](#deepracer-device-why-no-update-showing-up)
+ [Why Is My AWS DeepRacer Vehicle Not Connected to My Wi\-Fi Network?](#deepracer-device-why-vehicle-not-connected-to-wifi)
+ [Why Does the AWS DeepRacer Device Console Page Take a Long Time to Load?](#deepracer-device-why-device-console-page-takes-long-time-to-load)
+ [Why Does a Model Fail to Perform Well When Deployed to an AWS DeepRacer Vehicle?](#deepracer-device-why-deployed-model-fails-to-perform-as-well)

## Why Does the Video Player on the Device Console Not Show Video Stream from My Vehicle's Camera?<a name="deepracer-device-why-no-video-showing-on-device-console"></a>

 After logging into the AWS DeepRacer device console, you don't see in the video player in **Device Controls** any live video streamed from the camera mounted on the AWS DeepRacer vehicle\. This could happend because of the following issues: 
+ The camera might have a loose connection to the USB port\. Unplug the camera module from the vehicle, replug it into the USB port, power off and then power on the deivce to restart it\.
+ The camera might be defective\. Use a known working camera from another AWS DeepRacer vehicle, if available, to test if it's the case\.

## Why Does My AWS DeepRacer Vehicle Not Move?<a name="deepracer-device-why-vehicle-not-moving"></a>

You get your AWS DeepRacer vehicle, but can't make it to move\. This could happen because of the following issues: 
+  The vehicle's power bank is not turned on or the power bank is not connected to the vehicle\. Make sure to connect the provided USB\-C\-to\-USB C cable between the USB\-C port on the power bank and the USB\-C port on the vehcile chassis\. Verify that the LED indicators are lit for the charge levels on on the power bank\. If not, push the power button on the power bank, and then push the power button on the vehicle's chassis to boot up the device\. The device is booted up when its tail lights are lit\.
+ If the power bank is on and the vehicle is booted up, but the vehicle does not move in either manual or autonmous driving mode, check if the vehicle's battery under the vehicle chassis is charged and turned on\. If not, recharge the vehicle battery and turn it on\. 
+  The vehicle battery cable connector are not fully plugged into the device driving module power cable connector\. Make sure the cable connectors are tightly coupled\.
+ The battery cables are defective\. Test this battery on another working vehicle, if possible, to test if this is the case\.
+ The power switch of the vehicle battery is not turned on\. Make sure to turn the power switch on and hear two beeps followed by a long beep shortly after\. 

## Why Do I Not See the Latest Device Update and How I Get the Latest Update?<a name="deepracer-device-why-no-update-showing-up"></a>

Why is my AWS DeepRacer vehicle's software outdated? 
+ No automatic update is performed on the device lately\. You may need to perform a [manual update](deepracer-troubleshooting-manual-update-device.md)\. 
+ The vehicle is not connected to the Internet\. Make sure the vehicle is connected to a Wi\-Fi or Ethenet network with internet access\. 

## Why Is My AWS DeepRacer Vehicle Not Connected to My Wi\-Fi Network?<a name="deepracer-device-why-vehicle-not-connected-to-wifi"></a>

When I check the network status on the vehicle's OS, I don't see the AWS DeepRacer vehicle connected to any Wi\-Fi network\. This could happend because of the following issues: 
+ No Wi\-Fi has been configured for the AWS DeepRacer vehicle\. Follow this [setup instruction](deepracer-set-up-vehicle.md) to set up the Wi\-Fi network for your vehcile\.
+ The vehicle is out of the active network signal range\. Make sure to operate the vehicle within the chosen Wi\-Fi network range\.
+ The vehicle's pre\-configured Wi\-Fi network doesn't match the available Wi\-Fi network\. Follow the [setup instruction](deepracer-set-up-vehicle.md) to reset up the Wi\-Fi network that does not require active [captcha](https://en.wikipedia.org/wiki/CAPTCHA)\. 

## Why Does the AWS DeepRacer Device Console Page Take a Long Time to Load?<a name="deepracer-device-why-device-console-page-takes-long-time-to-load"></a>

When I tried to open the device console of my AWS DeepRacer vehicle, the device console page appears to take a long time to load\.
+ Your vehicle is down or off\. Make sure the vehicle is powered on when the tail lights are on\.
+ The IP address of you vehicle has changed, most likely by your network's DHCP server\. To find out the vehicle's new IP address, follow these [setup instructions](deepracer-set-up-vehicle.md) to sign in to the device console with the USB\-USB calbe connection between your computer and the vehicle\. View the new IP address in **Settings**\. Alternatively, you can examine the list of devices attached to your network to discover the new IP address\. If you're not a network administrator, ask the administrator to check it out for you\.

## Why Does a Model Fail to Perform Well When Deployed to an AWS DeepRacer Vehicle?<a name="deepracer-device-why-deployed-model-fails-to-perform-as-well"></a>

 After training a model and deploying its artifacts to my AWS DeepRacer vehicle, I sometimes see the vehicle doesn't perform as expected\. What went wrong? 

 In general, optimizing a trained model for transfer to a physical AWS DeepRacer vehicle is a challenging learning process\. It often requires iterations through trials and errors\. For general guidelines on the best practices, see [Optimize Training AWS DeepRacer Models for Real Environments](deepracer-console-train-evaluate-models.md#deepracer-evaluate-model-test-approaches)\. 

 The following are some likely common factors affecting the model performance in your AWS DeepRacer vehicle: 
+  Your model has not converged in training\. Clone the model to continue the training or retrain the model for a longer period of time\. Make sure the agent continuously finishes laps in the simulation, i\.e\., 100% process towards the end of the training\. 
+  Your model was over\-trained \(i\.e\., over\-fitted\)\. It fits too well to the training data, but doesn't generalize to unknown situtation\. Retrain the model with a more flexible or accomodating [reward function ](deepracer-console-train-evaluate-models.md#deepracer-train-models-define-reward-function) and/or increase the granularities of the [action space](deepracer-console-train-evaluate-models.md#deepracer-define-action-space-for-training)\. You should also evaluate a trained model on different tracks to see if the the model generalize well\. 
+  Your AWS DeepRacer vehicle may have not been calibrated properly\. To test if this is true, switch to manual driving and see if the vehicle drives as expected\. If not, [calibrate the vehicle](deepracer-calibrate-vehicle.md)\. 
+  You run the vehicle autonomously on a track that does not meet the requirements\. For track requirements, see [Build Your Physical Track for AWS DeepRacer](deepracer-build-your-track.md) 
+  There're too many objects close to the physical track, making the track significantly different from the simulated environment\. Clear the track surroundings to make the physical track as close to the simulated one possible\. 
+  Reflection from the track surface or a near\-by object can create glare to confuse the camera\. Adjust lighting and avoid making track on smooth\-surfaced concrete floors or with other shiny materials\. 