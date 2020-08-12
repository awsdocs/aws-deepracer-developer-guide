# Required IAM Roles for AWS DeepRacer to Call Dependent AWS Services<a name="deepracer-understand-required-permissions-and-iam-roles"></a>

Before you create a model, use the AWS DeepRacer console to set up resources for your account\. As you do this, the AWS DeepRacer console creates the following IAM roles:

[AWSDeepRacerServiceRole](https://console.aws.amazon.com/iam/home#/roles/AWSDeepRacerServiceRole)  
Allows AWS DeepRacer to create required resources and call AWS services on your behalf\.

[AWSDeepRacerSageMakerAccessRole](https://console.aws.amazon.com/iam/home#/roles/AWSDeepRacerSageMakerAccessRole)  
Allows Amazon SageMaker to create required resources and call AWS services on your behalf\.

[AWSDeepRacerRoboMakerAccessRole](https://console.aws.amazon.com/iam/home#/roles/AWSDeepRacerRoboMakerAccessRole)  
Allows AWS RoboMaker to create required resources and call AWS services on your behalf\.

[AWSDeepRacerLambdaAccessRole](https://console.aws.amazon.com/iam/home#/roles/AWSDeepRacerLambdaAccesseRole)  
Allows AWS Lambda functions to call AWS services on your behalf\.

[AWSDeepRacerCloudFormationAccessRole](https://console.aws.amazon.com/iam/home#/roles/AWSDeepRacerCloudFormationAccessRole)  
Allows AWS CloudFormation to create and manage AWS stacks and resources on your behalf\.

Follow the links to view detailed access permissions in the AWS IAM console\.