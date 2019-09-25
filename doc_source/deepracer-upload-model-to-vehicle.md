# Upload a Model to Your AWS DeepRacer Vehicle<a name="deepracer-upload-model-to-vehicle"></a>

To start your AWS DeepRacer vehicle on autonomous driving, you must have uploaded at least one AWS DeepRacer model to your AWS DeepRacer vehicle\. 

To upload a model, you must have [trained and evaluated the model](deepracer-console-train-evaluate-models.md)\. You can train the model using the AWS DeepRacer console\. After that, you need to download the model artifacts from its Amazon S3 storage to a \(local or network\) drive that can be accessed by your computer\.

**To upload a trained model to your vehicle**

1. Choose **Models** from the device console's main navigation pane\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-device-choose-models.png)

1. On the **Models** page, choose **Upload** above the **Models** list\. 

1. From the file picker, navigate to the drive or share where you've downloaded your model artifacts and choose the the compressed model file \(of the `*.tar.gz` extension\) to upload\.

   Only a successfully uploaded model will be added to the **Models** list and can be available for you to load it into the vehicle's inference engine in the autonomous driving mode\. For the instructions on how to load a model into your vehicle's inference engine, see [Drive Your AWS DeepRacer Vehicle Autonomously](deepracer-drive-your-vehicle.md#deepracer-drive-vehicle-autonomously)\.