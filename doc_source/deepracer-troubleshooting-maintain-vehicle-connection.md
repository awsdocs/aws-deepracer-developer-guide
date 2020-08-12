# How to Maintain Your Vehicle's Wi\-Fi Connection<a name="deepracer-troubleshooting-maintain-vehicle-connection"></a>

 The following troubleshooting guide provides you tips for maintaining your vehicle's connection\. 

## How to Troubleshoot Wi\-Fi Connection If Your Vehicle's Wi\-Fi LED Indicator Flashes Blue, Then Turns Red for Two Seconds, and Finally Off<a name="deepracer-troubleshoot-reconnect-wifi-after-led-turns-red-flashing-blue-and-off"></a>

Check the following to verify you have the valid Wi\-Fi connection settings\.
+ Verify that the USB drive has only one disk partition with only one *wifi\-creds\.txt* file on it\. If multiple *wifi\-creds\.txt* files are found, all of them will be processed in the order they were found, which may lead to unpredictable behavior\.
+ Verify the Wi\-Fi network's SSID and password are correctly specified in *wifi\-creds\.txt* file\. An example of this file is shown as follows:

  ```
  ###################################################################################
  #                                   AWS DeepRacer                                 # 
  # File name: wifi-creds.txt                                                       #
  #                                                                                 #  
  # ...                                                                             #
  ###################################################################################
  
  # Provide your SSID and password below
  ssid: ' MyHomeWi-Fi'
  password: myWiFiPassword
  ```
+ Verify both the field names of `ssid` and `password` in the *wifi\-creds\.txt* file are in lower case\.
+ Verify that each of the field name and value is separated by one colon \(:\)\. For example\. `ssid : ' MyHomeWi-Fi'`
+ Verify that the field value containing a space is enclosed by a pair of single quotes\. On Mac, TextEdit or some other text editor shows single quotes as of the '\.\.\.' form, but not of ‘\.\.\.’\. If the field value does not contain spaces, the value can be without single quotes\.

## What Does It Mean When the Vehicle's Wi\-Fi or Power LED Indicator Flashes Blue?<a name="deepracer-troubleshooting-failed-to-load-model-artifacts"></a>

If the USB drive contains *wifi\-creds\.txt* file, the Wi\-Fi LED indicator flashes blue while the vehicle is attempting to connect to the Wi\-Fi network specified in the file\.

If the USB drive has the `models` directory, the Power LED flashes blue while the vehicle is attempting to load the model files inside the directory\.

If the USB drive has both the *wifi\-creds\.txt* file and the `models` directory, the vehicle will process the two sequentially, starting with an attempt to connect to Wi\-Fi and then loading models\.

The Wi\-Fi LED might also turn red for two seconds if the Wi\-Fi connection attempt fails\.

## How Can I Connect to the Vehicle's Device Console Using its Hostname?<a name="deepracer-troubleshooting-connect-device-console-with-hostname"></a>

When connecting to the vehicle's device console using its hostname, make sure you type: `https://hostname.local` in the browser, where `hostname` value \(of the `AMSS-1234` format\) is printed on the bottom of the AWS DeepRacer vehicle\. \)

## How to Connect to Vehicle's Device Console Using Its IP Address<a name="deepracer-troubleshooting-connect-device-console-using-ip-address"></a>

To connect to the device console using IP address as shown in the *device\-status\.txt* file \(found on the USB drive\), make sure the following conditions are met\.
+  Check your laptop or mobile devices are in the same network as the AWS DeepRacer vehicle\. 
+  Check if you have connected to any VPN, if so, disconnect first\.
+  Try a different Wi\-Fi network\. For example, turn on personal hotspot on your phone\.