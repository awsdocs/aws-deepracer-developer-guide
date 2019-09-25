# How to Recover Your AWS DeepRacer Device Console Default Password?<a name="deepracer-troubleshooting-recover-device-web-server-password"></a>

Recovering your AWS DeepRacer device console default password involves retrieving or resetting the default password\. The default password is printed at the bottom of the device, as shown below\. 

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-troubleshooting-device-web-server-password.png)

Follow the instructions below to recover the password of your AWS DeepRacer device web server using a Ubuntu Terminal window\. 

1.  Connect your AWS DeepRacer device to a monitor\. You'll need a HDMI\-to\-HDMI, HDMI\-to\-DVI or similar cable and insert one end of the cable into the HDMI port on the vehicle's chassis and plug the other end into a supported display port on the monitor\. 

1.  Connect a USB keyboard to your AWS DeepRacer using the USB port on the device's compute module, after the compute module is booted\. 

1.  Type `deepracer` in the **Username** input field\. 

1.  Type the device SSH password in the **Password** input field\. 

   If this is your first time to log in to the device, type `deepracer` in the **Password** input field\. Reset the password, as required, before moving to the next step\. You'll use the new password for future logins\. For security reasons, use a complex or strong password phrase for the new password\.

1.  After logged in, open a Terminal window\. 

    You can use the Search button for the Terminal application\. 

1.  To get the default device console password, type the following command in the Terminal window: 

   ```
   $cat /sys/class/dmi/id/chassis_asset_tag
   ```

    The command outputs the default password as its result\. 

1. To reset the device console password to the default, run the following Python script from the Terminal window:

   ```
   sudo python /opt/aws/deepracer/nginx/reset_default_password.py
   ```