# My Battery is Charged but my AWS DeepRacer Vehicle Does Not Move<a name="deepracer-troubleshooting-immobile-vehicle-with-charged-battery"></a>

Follow these steps if your AWS DeepRacer console is set up, your compute battery is charged, and your wifi is connected, but your vehicle still does not move:

1. Lift the compute module, being careful not to loosen the wires connecting it to the drive train\. Make sure the vehicle battery underneath is correctly connected, red input to red adapter\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-connect-vehicle-battery.png)

1. Turn on the vehicle drive train by pushing the switch to the "on" position\. Listen for the indicator sound\-\-two short beeps\-\-to confirm that the car has charge\. If the car powers on successfully, skip to step 4\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-troubleshooting-drive-module-battery-switch.png)

1. If you do not hear two beeps when you switch on your car battery, ensure that the battery is fully charged\. When both red and green lights on the vehicle battery charge adapter are lit, it indicates that the battery still needs charging\. When only the green light is illuminated, your battery is fully charged and ready to use\. See [How to Charge the AWS DeepRacer Drive Module Battery?](deepracer-troubleshooting-charge-vehicle-battery-first-time.md) for more help\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-troubleshooting-vehicle-battery-charger-LEDs.png)

   *Red light \+ green light = *not* fully charged*

1. Connect your car to [wifi](deepracer-set-up-vehicle.md) and open the AWS DeepRacer console in your browser\. Manually drive your vehicle with the touch joystick to confirm that it can move\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/Deepracer-troubleshooting-manually-drive-with-touch-joystick.png)

**REMINDER: **To get the most millage out of your car battery, make sure to switch off the vehicle drive train or disconnect its battery when you are not using your AWS DeepRacer\.

If your car still does not move, contact AWSDeepRacer\-Help@amazon\.com\.