# How to Get the MAC Address of Your AWS DeepRacer Device<a name="deepracer-troubleshooting-get-mac-address"></a>

Follow the instructions below to get the MAC address of your AWS DeepRacer device: 

1.  Make sure that your AWS DeepRacer device is only connected to a Wi\-Fi network\. 

1.  Connect your AWS DeepRacer device to a monitor\. You'll need a HDMI\-to\-HDMI, HDMI\-to\-DVI or similar cable and insert one end of the cable into the HDMI port on the vehicle's chassis and plug the other end into a supported display port on the monitor\. 

1.  Connect a USB keyboard to your AWS DeepRacer using the USB port on the device's compute module, after the compute module is booted\. 

1.  Type `deepracer` in the **Username** input field\. 

1.  Type the device SSH password in the **Password** input field\. 

     

   If this is your first time to log in to the device, type `deepracer` in the **Password** input field\. Reset the password, as required, before moving to the next step\. You'll use the new password for future logins\. For security reasons, use a complex or strong password phrase for the new password\.

1.  After logged in, open a Terminal window\. 

    You can use the Search button for the Terminal application\. 

1.  Type the following Ubuntu shell command in the Terminal window: 

   ```
   ifconfig | grep HWaddr
   ```

    The command produces an output similar to the following: 

   ```
   mlan0    Link encap:Ethernet   HWaddr   01:2a:34:b5:c6:de
   ```

    The hexadecimal numbers are the device's MAC address\. 