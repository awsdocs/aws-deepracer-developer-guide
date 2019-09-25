# Choose a Wi\-Fi Network for Your AWS DeepRacer Vehicle<a name="deepracer-set-up-vehicle"></a>

The first time you open your AWS DeepRacer vehicle, you must set it up to connect to a Wi\-Fi network\. Complete this setup to get the vehicle's software updated and to get the IP address to access the vehicle's device console\. 

This section walks you through the steps to perform the following tasks:
+ Connect your laptop or desktop computer to your vehicle\.
+ Set up the vehicle's Wi\-Fi connection\. 
+ Update the vehicle's software\.
+ Get the vehicle's IP address\. 
+ Test drive the vehicle\.

Use a laptop or desktop computer to perform the setup tasks\. We'll refer to this setup computer as your computer, to avoid possible confusion with the vehicle's compute module, which is running the Ubuntu operating system\. 

After the initial setup of the Wi\-Fi connection, you can follow the same instructions to choose a different Wi\-Fi network\.

**Note**  
 AWS DeepRacer does not support Wi\-Fi network that requires active [captcha](https://en.wikipedia.org/wiki/CAPTCHA) verification for use sign\-in\. 

**Topics**
+ [Get Ready to Set Up Wi\-Fi Connection for Your AWS DeepRacer Vehicle](#deepracer-set-up-vehicle-connect-computer-with-vehicle)
+ [Set Up Wi\-Fi Connection and Update Your AWS DeepRacer Vehicle's Software](#deepracer-set-up-vehicle-wifi-connection)

## Get Ready to Set Up Wi\-Fi Connection for Your AWS DeepRacer Vehicle<a name="deepracer-set-up-vehicle-connect-computer-with-vehicle"></a>

To set up your vehicle's Wi\-Fi connection, connect your a laptop or desktop computer to your vehicle's compute module using the included *USB\-to\-USB C* cable\. 

To connect your computer to your vehicle's compute module, follow the steps below\.

**To connect your computer to your vehicle to set up the device**

1. Insert the USB end of the *USB\-to\-USB C* cable into your computer's USB port\. 

1. Insert the cable's USB C end into your vehicle's USB C port\.

You're now ready to proceed to setting up your vehicle's Wi\-Fi connection\.

## Set Up Wi\-Fi Connection and Update Your AWS DeepRacer Vehicle's Software<a name="deepracer-set-up-vehicle-wifi-connection"></a>

Before you follow the steps here to set up the Wi\-Fi connection, be sure you complete the steps in [Get Ready to Set Up Wi\-Fi Connection for Your AWS DeepRacer Vehicle](#deepracer-set-up-vehicle-connect-computer-with-vehicle)\.

1. Look at the bottom of your vehicle and make note of the password printed under **Host name**\. You'll need it to log in to the device control console to perform the setup\.

1. On your computer, go to `https://deepracer.aws` to launch the device control console of your vehicle\.

1. When prompted with a message that the connection is not private or secure, do one of the following\. 

   1. In Chrome, choose **Avanced** and then choose **Proceed to *<device\_console\_ip\_address>* \(unsafe\)**\.

   1. In Safari, choose **Details**, follow the **visit this website** link, and the choose **Visit Websites**\. If prompted for your password to update the certificate trust settings, type the password and then choose **Update settings**\.

   1. In Opera, choose **Continue Anyway** when warned of an invalid certificate\.

   1. In Edge, choose **Details** and then choose **Go on to the webpage \(Note recommended\)**\.

   1. In Firefox, choose **Advanced**, choose **Add Exception**, and then choose **Confirm Security Exception**\.

1.  Under **Unlock your AWS DeepRacer vehicle**, enter the password noted in **Step 1** and then choose **Access vehicle**\.

1. On the **Connect your vehicle to your Wi\-Fi network** pane, choose your Wi\-Fi network name from the **Wi\-Fi network name \(SSID\)** drop\-down menu, type the password of your Wi\-Fi network under **Wi\-Fi password**, and choose **Connect**\.

1. Wait until the Wi\-Fi connection status changes from **Connecting to Wi\-Fi network\.\.\.** to **Connected**\. Then, choose **Next**\.

1. On the **Software update** pane, if a software update is required, turn on the vehicle's compute module, with the included power cord and power adapter, and then choose **Install software update**\. 

    Powering the vehicle with an external power source helps avoid interruption of the software update if the compute module's power bank become discharged\.

1. Wait until the software update status changes from **Installing software update** to **Software update installed successfully**\.

1. Note the IP address shown under **Wi\-Fi network details**\. You'll need it to open the vehicle's device control console after the initial setup and any subsequent modification of the Wi\-Fi network settings\. 