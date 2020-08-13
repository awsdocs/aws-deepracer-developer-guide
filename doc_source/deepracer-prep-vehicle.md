# Get to Know Your AWS DeepRacer Vehicle<a name="deepracer-prep-vehicle"></a>

 Your AWS DeepRacer vehicle is a machine learning\-enabled, battery\-powered, and Wi\-Fi\-connected 1/18th\-scale model four\-wheel drive car with a front\-mounted 4\-megapixel camera and an Ubuntu\-based compute module\. 

The vehicle can drive autonomously by running inference that is based on a reinforcement learning model in its compute module\. You can also drive the vehicle manually, without deploying any reinforcement learning model\. If you have not already obtained an AWS DeepRacer vehicle, you can [order one here](https://www.amazon.com/AWS-DeepRacer-Fully-autonomous-developers/dp/B07JMHRKQG)\.

The AWS DeepRacer vehicle is powered by a brushed motor\. The driving speed is controlled by a voltage regulator that controls how fast the motor spins\. The [servomechanism \(servo\)](https://en.wikipedia.org/wiki/Servomechanism) that operates the steering system is protected by the black cover in the AWS DeepRacer vehicle chassis\.

**Topics**
+ [Inspect Your AWS DeepRacer Vehicle](#deepracer-prep-vehicle-inspect-components)
+ [Charge and Install Your AWS DeepRacer Batteries](#deepracer-prep-vehicle-charge-battery-power-bank)
+ [Test Your AWS DeepRacer Compute Module](#deepracer-prep-vehicle-test-compute-module)
+ [Turn Off Your AWS DeepRacer Vehicle](#deepracer-shutdown-device)
+ [AWS DeepRacer Vehicle LED Indicators](deepracer-vehicle-led-indicators.md)
+ [AWS DeepRacer Vehicle Spare Parts](deepracer-vehicle-chassis-parts.md)

## Inspect Your AWS DeepRacer Vehicle<a name="deepracer-prep-vehicle-inspect-components"></a>

When you open your AWS DeepRacer vehicle box, you should find the following components and accessories: 

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-what-is-in-the-box.png)


****  

| Components | Comments | 
| --- | --- | 
| Vehicle Chassis \[1\] | Includes a front\-mounted camera for capturing vehicle driving experiences and the compute module for autonomous driving\. You can view images captured by the camera as a streaming video on the vehicle's device console\. The chassis includes a brushed electric motor, an electronic speed controller \(ESC\), and a servomechanism \(servo\) | 
| Vehicle body shell \[2\] | Remove this when setting up the vehicle\. | 
| Micro\-USB to USB\-A cable \[3\] | Use this to support [USB\-OTG](https://en.wikipedia.org/wiki/USB_On-The-Go) functionality\.  | 
| Compute battery \[4\] | Use this to power the compute module that runs inference on a downloaded AWS DeepRacer reinforcement learning model\. | 
| Compute battery connector cable \[5\] | Use this USB\-C to USB\-C cable to connect the compute module with the battery\. If you have a Dell compute battery, this cable will be longer\. | 
| Power cable \[6a\]  | Use this to connect the power adaptor to a power outlet\. | 
| Power adapter\[6b\]  | Use this to charge the compute battery and the compute module\. | 
| Pins \(spare parts\) \[7\] | Use to fasten the compute module to the vehicle chassis\. These are extras\. | 
| Vehicle battery \[8\] |  A 7\.4v LiPo battery pack to power the motor\.  | 
| Vehicle battery charge adapter \[9a\] | Use this to charge the vehicle battery that powers the vehicle drive chain\. | 
| Vehicle battery charge cable \[9b\] | Use this to connect the vehicle battery charger to a power outlet\. | 
| Battery unlock cable \[10\] | Use this if your battery enters lock out state\. | 

To set up your AWS DeepRacer vehicle, you must also have the following items ready: 
+ A computer with a USB port and access to the internet\.
+ A Wi\-Fi network connected to the internet\.
+ An AWS account\.

Now follow the instructions in the [next section](#deepracer-prep-vehicle-charge-battery-power-bank) to make sure your vehicle battery and the power bank are charged\.

## Charge and Install Your AWS DeepRacer Batteries<a name="deepracer-prep-vehicle-charge-battery-power-bank"></a>

Your AWS DeepRacer vehicle has two power sources: the vehicle battery and the compute module power bank\.

The power bank keeps the compute module running\. The compute module maintains the Wi\-Fi connection, runs inference against a deployed AWS DeepRacer model, and issues a command for the vehicle to take an action\.

 The vehicle battery powers the motor to move the vehicle\. It has two sets of cables\. The two\-wired set of the red and black cables is used to connect to the vehicle's ESC and the triple\-wired blue \(or black\), white and red cables is to connect to the charger\. For driving, only the two\-wired cable set should be connected to the vehicle\. 

After fully charged, the battery voltage will drop as the batteries discharge\. When the voltage drops, the available torque also drops\. As a consequence, the same speed setting will result in slower speed on the track\. When the battery is fully empty, the vehicle stops moving\. For autonomous driving under normal conditions, the battery usually lasts 15\-25 minutes\. To ensure consistent behavior, it is recommended that you charge the battery after every 15 minutes of use\. 

To install and charge the vehicle battery and the power bank, follow the steps below\.

1. Remove your AWS DeepRacer vehicle shell\.

1. Remove the four vehicle chassis pins\. Carefully lift vehicle chassis while keeping wires connected\.

1. To charge and install the vehicle battery, do the following:

   1.  To charge the battery, plug the three\-wired cable set from the batter to the charger to connect the battery to the power adapter and then plug the power adapter to a wall outlet or to a USB port if a USB cable is used to charge the battery\. 

       For a graphical illustration of how to charge the vehicle battery using the enclosed charger, see [How to Charge the AWS DeepRacer Drive Module Battery](deepracer-troubleshooting-charge-vehicle-battery-first-time.md)\. 

   1. After the battery is charged, plug the two\-wired cable set of the vehicle battery cable into the black and red cable connector on your vehicle\. 

   1. To secure the vehicle battery, tie the battery under the vehicle chassis with the attached straps\.

      Make sure to keep all the cables inside the vehicle\.

   1. To check if the vehicle battery is charged, do the following: 

      1. Slide the vehicle power switch to turn on the vehicle\.

      1. Listen for two short beeps\.

          If you don't hear the beeps, the vehicle is not charged\. Remove the battery from the vehicle and repeat Step 1 above to recharge the battery\. 

      1. When not using the vehicle, slide the vehicle power switch back to turn off the vehicle battery\.

1. To check the power bank charging level, do the following: 

   1. Press the power button on the power bank\.

   1. Check the four LED lights next to the power button to determine the charging level\.

      If all the four LED lights are lit, the power bank is fully changed\. If none of the LED lights are lit, the power bank needs to be charged\. 

   1. To charge the power bank, insert the USB C plug from the power adapter into the USB C port of the power bank\. It takes some time for the power bank to be fully charged\. When it is charged, repeat **Step 4** to confirm that the power bank is fully charged\.

1. To install the power bank, do the following:

   1. Insert the power bank into its holder with the power button and USB C port facing the back of the vehicle\.

   1. Use the strap to tie the power bank to the vehicle chassis securely\.
**Note**  
Do not connect the power bank to the compute module in this step\.

## Test Your AWS DeepRacer Compute Module<a name="deepracer-prep-vehicle-test-compute-module"></a>

Test the compute module to verify that it can be started successfully\. To test the module by using an external power source, follow the steps below:

**To test your vehicle's compute module**

1. Connect the compute module to a power source\. Connect the power cord to the power adapter, plug the power cord to a power outlet, and insert the power adapter's USB C plug into the USB C port on the compute module\.

1. Turn on the vehicle's compute module by pressing the power button on the compute module\.

1. To verify the compute module's status, check that the LED lights are shown as follows:
   + Solid blue

     The compute module is started, connected to the specified Wi\-Fi, and ready to go\. 

     In this state, you can log in to the compute module after you attach it to a monitor using an HDMI cable, a USB mouse and a USB keyboard\. For the first\-time login, use `deepracer` for both the **username** and **password**\. You will then be asked to reset the password for future logins\. For security reasons, choose a strong password phrase for the new password\.
   + Blinking red

     The compute module is in setup mode\. 
   + Solid yellow

     The compute module is initializing\.
   + Solid red

     The compute module failed to connect to the Wi\-Fi network\.

1. When you're done with the test, press the power button on the compute module to turn it off and then unplug it from the external power source\.

## Turn Off Your AWS DeepRacer Vehicle<a name="deepracer-shutdown-device"></a>

To turn off your AWS DeepRacer vehicle, unplug the vehicle from the external power source\. You can also press the power button on the device until power indicator is off\. 