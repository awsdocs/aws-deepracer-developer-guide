# My AWS DeepRacer reinforcement learning model is failing to import during the service update<a name="deepracer-troubleshooting-service-migration-errors"></a>

## What is being updated?<a name="what-is-update"></a>

AWS DeepRacer is updating our service architecture to provide more cost\-effective, flat fee pricing and simplified billing\. We are migrating \(moving\) the training, evaluation, and storage of your reinforcement learning \(RL\) models from your AWS S3 bucket to the AWS DeepRacer console\. After the update, you will make API calls to AWS DeepRacer directly, instead of AWS DeepRacer calling related AWS services, like SageMaker and RoboMaker on your behalf\. This will be reflected by a new flat fee model in your monthly AWS DeepRacer bill, where you'll no longer see separate charges for underlying services\. Instead, there will be one entry with two categories, service use and model storage\.

Learn more about AWS DeepRacer pricing [here](http://aws.amazon.com/deepracer/pricing/)\.

## What will happen to my RL models?<a name="RL-models"></a>

AWS DeepRacer models you trained before the update are automatically moved \(copied and validated\) from Amazon S3 to the AWS DeepRacer console\. Models being moved will be unavailable until they are validated\. Starting August 10th models that were moved will be removed from your Amazon S3, to prevent double billing for storage of the same model\. AWS DeepRacer storage is free in July and August 2020 while we move your models\. After the update you can manage your models \(delete, download, or import\) from the AWS DeepRacer console in the **Your models** section\.

Models that encountered errors during the process will not be usable in the AWS DeepRacer console and will not be removed from your Amazon S3\. Please follow the steps in the AWS DeepRacer console to resolve the errors\. If you want to import models manually at a later date, you can use the **Import **button in the AWS DeepRacer console\. 

## What else changes?<a name="log-files-buttons"></a>

You will not see your AWS DeepRacer training or evaluation jobs listed in Amazon SageMaker or AWS RoboMaker anymore\. To ensure you get the data needed to keep improving your models, we have added buttons in the console that you can use to easily download the training and simulation log files\.

## Troubleshooting<a name="quick-help"></a>

If your model fails to copy to the AWS DeepRacer service account, find your error message and follow the steps\. Learn more in the related help topic\.


| Service error | Speak to me in Human | Which means\.\.\. | 
| --- | --- | --- | 
| SERVICE\_ERROR | Model copy error: Retry update\. | We couldn't copy your model despite making several attempts\. If the model is still in your S3 bucket, retry by selecting the model, and choosing Update\. Or, manually import it\. For more information, see [What is being updated?](#what-is-update)\. To remove this message, select the model, and choose Delete\. | 
| SRC\_BUCKET\_DOES\_NOT\_EXIST | Bucket doesn't exist: Import model manually\. | We couldn't copy the model during the update because the S3 bucket where this model was stored has been deleted\. If you still have a copy of the model, place it in S3, and manually import it from Amazon S3\. For more information, see [Expected permissions](#bucket-policy)\. To remove this message, select the model, and choose Delete\. | 
| ACCESS\_DENIED\_TO\_BUCKET | Can't access bucket: Restore bucket permissions\. | The permissions for the S3 bucket where this model is stored have changed, so we couldn't copy the model during the update\. To restore the bucket permissions, see [S3 folder structure](#s3-folder-structure)\. After restoring permissions, try updating the model again\. To remove this message, select the model, and choose Delete\. | 
| COACH\_CHECKPOINT\_DOES\_NOT\_EXIST | Coach file doesn't exist: Import model manually\. | We can't copy the model because the coach checkpoint metadata has been deleted from the S3 bucket\. If you still have the file, try to restore it and choose Update\. Or, manually import the model\. For more information, see [Model import](#model-import)\. To remove this message, select the model, and choose Delete\. | 
| MODEL\_TAR\_FILE\_SIZE\_LIMIT\_EXCEEDED | Model file too large: Import model manually\. | Your model file exceeds the file size limit that the service can create, thus your file was edited\. This model will not be imported\. For more information, see [S3 folder structure](#s3-folder-structure)\. To remove this message, select the model, and choose Delete\. | 
| CHECKPOINT\_FILE\_SIZE\_LIMIT\_EXCEEDED | Checkpoint file too large: Import model manually\. | Your checkpoint file exceeds the file size limit that the service can create, thus your file was edited\. This model will not be imported\. For more information, see [S3 folder structure](#s3-folder-structure)\. To remove this message, select the model, and choose Delete\. | 
| JSON\_YAML\_FILE\_SIZE\_LIMIT\_EXCEEDED | Metadata file too large: Import model manually\. | Your YAML file exceeds the file size limit that the service can create, thus your file was edited\. This model will not be imported\. For more information, see [S3 folder structure](#s3-folder-structure)\. To remove this message, select the model, and choose Delete\. | 
| FILE\_DOES\_NOT\_EXIST | File doesn't exist: Import model manually\. | We can't copy the model because it's been deleted from the S3 bucket\. If you still have the file, try to restore it, and then choose Update\. Or, manually import the model\. For more information, see [S3 folder structure](#s3-folder-structure)\. To remove this message, select the model, and choose Delete\. | 
| S3\_COPY\_ERROR | Model copy error: Retry update\. | We couldn't copy your model despite making several attempts\. If the model is still in your S3 bucket, retry by selecting the model, and choosing Update\. Or, manually import the model\. For more information, see [S3 folder structure](#s3-folder-structure)\. To remove this message, select the model, and choose Delete\. | 
| CHECKPOINT\_FILES\_DOES\_NOT\_EXIST | Checkpoint doesn't exist: Import model manually\. | We can't copy the model because the checkpoint file has been deleted from the S3 bucket\. If you still have the file, restore it to S3, select the model, and chose Update\. Or, manually import the model\. For more information, see [S3 folder structure](#s3-folder-structure)\. To remove this message, select the model, and choose Delete\. | 
| MODEL\_VALIDATION\_SERVICE\_ERROR | Invalid model: Import model manually\. | We can't validate your model because it's been edited\. If you have a copy of it, import it manually\. For more information, see [S3 folder structure](#s3-folder-structure)\. To remove this message, select the model, and choose Delete\. | 
| ACCOUNT\_RESOURCE\_DOES\_NOT\_EXIST | Missing or incorrect permissions: Reset permissions\. | We can't copy the model because the permissions that were available with AWS DeepRacer when you trained it have been removed\. To authorize AWS DeepRacer to recreate the required permissions, choose the model and then choose Update\. After recreating the permissions, AWS DeepRacer will copy the model\. For more information, see [S3 folder structure](#s3-folder-structure)\. | 

## Prerequisites for Importing a Model<a name="model-import-prerequites"></a>

In order to import an RL model you trained: 
+ Include all necessary[ model files](#model-files) named with appropriate conventions\.
+ Locate files as expected within the Amazon [S3 folder structure](#s3-folder-structure)\.
+ Include a valid [S3 bucket policy](#bucket-policy) and all necessary[ import permissions](#import-model-permissions)\.

When you have all the necessary files in the expected folders, follow the [import model](#model-import) instructions\.

## Model files<a name="model-files"></a>

**Mandatory \- your AWS DeepRacer RL models need to include these files for a successful import\. Follow the steps in [S3 folder structure](#s3-folder-structure) to make sure they exist in the correct folders\.**
+ `.coach_checkpoint` \- The \.coach\_checkpoint file is a pointer file containing the name of the checkpoint that will be imported\. The following code shows an example of a \.coach\_checkpoint file, which is one line and contains a key name\.

  ```
  13_Step-25173.ckpt
  ```
+ `*ckpt*`files \- Checkpoint file names use the naming convention, `number of training iteration_Step-total steps.ckpt`\. The following code shows example checkpoints\.

  ```
            
  1_Step-42.ckpt,
  2_Step-91.ckpt,
  3_Step-124.ckpt,
  4_Step-162.ckpt
  ```
+ `model_metadata.json` \- Your model\_metadata\.json file contains descriptive information about your model\. The following code shows an example of the contents of a model\_metadata\.json file\.

  ```
  {
      "action_space": [
          {
              "steering_angle": -30,
              "speed": 0.5,
              "index": 0
          },
          {
              "steering_angle": -30,
              "speed": 1,
              "index": 1
          },
          {
              "steering_angle": 30,
              "speed": 1,
              "index": 9
          }
      ],
      "sensor": [
          "FRONT_FACING_CAMERA"
      ],
      "neural_network": "DEEP_CONVOLUTIONAL_NETWORK_SHALLOW",
      "version": "3"
  }
  ```
+ `reward_function.py`
+ `model.tar.gz`

**Optional \- your model will import without these files, but we need them to render your training and evaluation metrics\.**
+ `deepracer_checkpoints.json` \- If this file is present then `.coach_checkpoint` will be ignored\. The following code is an example that shows the json format that a `.coach_checkpoint` file needs to be in for your model to import successfully\.

  ```
   {"best_checkpoint": {"name": "319_Step-43282.ckpt"}, "last_checkpoint": {"name": "20_Step-43482.ckpt"}}
  ```
+ `training_params.yaml`
+ `EvaluationMetrics*.json`
+ ` TrainingMetrics*.json`

## Finding checkpoint files<a name="checkpoint-files"></a>

When we import your model, we check whether the following checkpoint files are present in this order:

1. `deepracer_checkpoints.json` \- The following code is an example that shows the json format that a `.coach_checkpoint` file needs to be in for your model to import successfully\.

   ```
    {"best_checkpoint": {"name": "319_Step-43282.ckpt"}, "last_checkpoint": {"name": "20_Step-43482.ckpt"}}
   ```

1. `.coach_checkpoint` \- The `.coach_checkpoint` file is a pointer file containing the name of the checkpoint that will be imported\. The following code shows an example of the contents of a checkpoint file, which is one line and contains a key name\.

   ```
   13_Step-25173.ckpt
   ```

If `deepracer_checkpoints.json` is present, but we can't find the named checkpoints in the file, the import will fail:

```
# We can find a deepracer_checkpoints.json file in the S3 containing the model you want to import:
{"best_checkpoint": {"name": "319_Step-43282.ckpt"}, "last_checkpoint": {"name": "20_Step-43482.ckpt"}}

# We CAN'T find the named checkpoints in the file:
320_Step-43278.ckpt
321_Step-43280.ckpt
322_Step-43282.ckpt

# The import fails. :-(
```

If `.coach_checkpoint` is present, but we can't find the named checkpoint in the file, the import will fail:

```
# We can find a .coach_checkpoint file in the S3 containing the model you want to import:
13_Step-25173.ckpt

# We CAN'T find the named checkpoints in the file:
13_Step-25174.ckpt
13_Step-25175.ckpt
14_Step-3456.ckpt

# The import fails. :-(
```

If neither `deepracer_checkpoints.json` nor `.coach_checkpoint` files are present, the import will fail\.

To ensure your import is a success, check that your `.coach_checkpoint` is in the model folder of your model's S3 bucket\. Next, make sure the checkpoint called out in the `.coach_checkpoint` file is present and the key names of the checkpoint files follow the naming convention `number of training iteration_Step-total steps.ckpt`\.

```
# We can find a .coach_checkpoint file in the S3 containing the model you want to import:
13_Step-25173.ckpt

# We CAN find the named checkpoints in the file:
13_Step-25173.ckpt
13_Step-25174.ckpt
13_Step-25175.ckpt
14_Step-3456.ckpt

# The import succeeds. :-)
```

## Checkpoint logic<a name="checkpoint-logic"></a>

When a `deepracer_checkpoints.json` file exists, we copy the `best_checkpoint` and `last_checkpoint` files using the keys from your `deepracer_checkpoints file`\.

When only a `.coach_checkpoint file exists`, we copy the specified checkpoint\. The following code shows example checkpoints inside a `coach_checkpoint` file\.

```
          
1_Step-42.ckpt,
2_Step-91.ckpt,
3_Step-124.ckpt,
4_Step-162.ckpt
```
+ `The .coach_checkpoint` file in the example contains `4_Step-162.ckpt`\.
+ `A deepracer_checkpoints.json` file isn't present\.
+ So we copy the last two checkpoints, `3_Step-124.ckpt` and `4_Step-162.ckpt` \.

The following code shows a different example of the contents of `coach_checkpoint` file\.

```
3_Step-124.ckpt.data-00000-of-00001,
3_Step-124.ckpt.index,
3_Step-124.ckpt.meta,
4_Step-162.ckpt.index,
4_Step-162.ckpt.meta
4_Step-162.ckpt.data-00000-of-00001
```

Checkpoint file names use the naming convention, `number of training iteration_Step-total steps.ckpt`, so in this example, we make an S3:list call\. This means we copy all the `3_Step-124.ckpt*` files and `4_Step-162.ckpt*` files to find the second from the last checkpoint\. 

## S3 folder structure<a name="s3-folder-structure"></a>

This section identifies what your Amazon S3 folder structure should look like to complete the import process successfully\. Use this guide to check that you have all the necessary files in the correct folders and retry the import\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-model-import-file-structure.png)

**Check your folder structure and make sure your files are in the correct folder\.**

1. Open **S3** in the AWS management console\. Choose the S3 bucket `aws-deepracer-XxXXXxxX-xXXx-XxXX-XXxX-xXXXXxxXXxX` that contains the model you want to import or migrate\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/customer-s3-bucket-I.png)

1. In the model's S3 bucket, choose the model **S3 prefix** `DeepRacer-SageMaker-RoboMaker-comm-XXXXXXXXXXXX-XXXXXXXXXXXXXX-xxxxxXxX-xxXx-XXxx-xXXX-XXxXxXXXXxXX` for the model you want to import or migrate\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/customer-specific-model-II.png)

1. In the **prefix root** folder, observe your **ip** and **model** folders\. You should also see your model's `training_params.yaml` and `reward_function.py` files\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/customer-file-structure-III.png)

1. Open your **ip** folder to check that it contains your `hyperparameters.json` file\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/customer-hyperperameters-IV.png)

1. When your `hyperparameters.json` file is in place, navigate back one level to your **S3 prefix** root folder\.

1. Open your **model** folder to make sure it contains all the necessary model artifacts\. Your `.coach_checkpoint` file should be in this folder\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/customer-coach-checkpoint-V.png)

1. When all of your files are in the correct folders, go back to the AWS DeepRacer console and retry the import or migration\.

## S3 bucket policy<a name="bucket-policy"></a>

The permissions for the S3 bucket where your model is stored have changed, so we couldn't copy the model during the update\. This can happen for two reasons, you directly edited the permissions on the AWS DeepRacer S3 or the AWS DeepRacer service role policy\.

If you directly edited the permissions on your DeepRacer S3, restore your bucket permissions with the following policy:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Stmt1586917903457",
            "Effect": "Allow",
            "Principal": {
                "Service": ""deepracer.amazonaws.com"
                },
            "Action": [
                "s3:GetObjectAcl",
                "s3:GetObject",
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": [
               "arn:aws:s3:::your-bucket-name",
               "arn:aws:s3:::your-bucket-name/*"
            ]
        }
    ]
}
```

After restoring permissions, try updating the model again\.

If you directly edited the AWS DeepRacer service role policy, select the model with the `ACCESS_DENIED_TO_BUCKET` error and choose **Update**\. This recreates the IAM service role and reattempts to migrate the model\.

To remove this message, select the model, and choose **Delete**\.

## Model import permissions<a name="import-model-permissions"></a>

If you have modified your role and policy, make sure the managed policy at minimum includes the following permissions:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListAllMyBuckets"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:PutBucketPolicy",
                "s3:GetBucketPolicy",
                "s3:ListBucket",
                "s3:GetBucketAcl",
                "s3:GetObject",
                "s3:GetObjectVersion",
                "s3:GetObjectAcl",
                "s3:GetBucketLocation"
            ],
            "Resource": [
                "arn:aws:s3:::your-bucket-name",
                "arn:aws:s3:::your-bucket-name/*"
            ]
        }
    ]
}
```

The role needs to have the below trust policy:

```
             {
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "deepracer.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

## How to Import a Model from SageMaker<a name="model-import"></a>

To import an RL Model from SageMaker:

1. In the AWS DeepRacer console, choose **Import model**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-import-model.png)

1. Input the following:
   + Model name
   + Model description
   + Model s3 bucket and prefix
   + Role to be assumed to import the model

**Note**  
On macOS and iOS, files starting with a "\.", such as \.coach\_checkpoint, are hidden\. To make these essential files visible, in Finder, press Command\+Shift\+Dot\. Then move them to your S3 bucket so they are included in your import\.

If your model fails to import, follow the instructions given in the error message and select the ** retry import** button in the AWS DeepRacer console\.

## Model migration permissions<a name="migration-permissions"></a>

The managed policy needs to have the below permissions at minimum\. This shouldn't be an issue unless you modified your permissions:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListAllMyBuckets"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:PutBucketPolicy",
                "s3:GetBucketPolicy",
                "s3:ListBucket",
                "s3:GetBucketAcl",
                "s3:GetObject",
                "s3:GetObjectVersion",
                "s3:GetObjectAcl",
                "s3:GetBucketLocation"
            ],
            "Resource": [
                "arn:aws:s3:::*deepracer*",
                "arn:aws:s3:::*deepracer*/*"
            ]
        }
    ]
}
```

The role needs to have the below trust policy:

```
             {
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "deepracer.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```