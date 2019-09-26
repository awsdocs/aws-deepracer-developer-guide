# AWS DeepRacer Vehicle LED Indicators<a name="deepracer-vehicle-led-indicators"></a>

 Your AWS DeepRacer vehicle has two sets of LED indicators for the vehicle status and for customizable visual identification of your vehicle, respectively\. 

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-vehicle-led-indicators.png)

 The details are discussed as follows\. 

**Topics**
+ [AWS DeepRacer Vehicle System LED Indicators](#deepracer-vehicle-led-indicators-system)
+ [AWS DeepRacer Vehicle Identification LEDs](#deepracer-vehicle-led-indicators-custom)

## AWS DeepRacer Vehicle System LED Indicators<a name="deepracer-vehicle-led-indicators-system"></a>

 The AWS DeepRacer vehicle system LED indicators are located on the left side of the vehicle chassis when the vehicle is in the forward position in front of you\. 

 The three system LEDs are positioned after the **RESET** button\. The first LED \(on the left side of your field of view\) shows the status of the system power\. The second \(middle\) LED is reserved for future use\. The last \(right\) LED shows the status of the Wi\-Fi connection\. 


****  

| LED Type | Color | Status | 
| --- | --- | --- | 
| Power | Off | There is no power supply\. | 
|  | Blinking yellow | BIOS and OS are being loaded\. | 
|  | Steady yellow | OS is loaded\. | 
|  | Steady blue | An application is running\. | 
|  | Blinking blue | A software update is in progress\. | 
|  | Steady red |  An error is encountered while the system is being booted or an application is being started\.  | 
| Wi\-Fi | Off | There is no Wi\-Fi connection\. | 
|  | Blinking blue | The vehicle is connecting to the Wi\-Fi network\. | 
|  | Steady red for 2 seconds and then off | The Wi\-Fi connection failed\. | 
|  | Steady blue | The Wi\-Fi connection is established\. | 

## AWS DeepRacer Vehicle Identification LEDs<a name="deepracer-vehicle-led-indicators-custom"></a>

The AWS DeepRacer vehicle custom LEDs are located at the tail of the vehicle\. They're used to help identifying your vehicle in races when multiple vehicles are present\. You can use the AWS DeepRacer device console to [set them a supported color](deepracer-manage-vehicle-settings.md) of your choosing\.