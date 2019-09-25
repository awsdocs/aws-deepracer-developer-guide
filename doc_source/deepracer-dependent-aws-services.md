# AWS DeepRacer\-Dependent AWS Services<a name="deepracer-dependent-aws-services"></a>

 AWS DeepRacer uses the following AWS services to manage required resources:

Amazon Simple Storage Service  
To store trained model artifacts in an Amazon S3 bucket\. 

AWS Lambda  
To create and run the reward functions\. 

AWS CloudFormation  
To create training jobs for AWS DeepRacer models\.

Amazon SageMaker  
To train the AWS DeepRacer models\.

AWS RoboMaker  
To simulate an environment for both training and evaluation\.

 The dependent AWS Lambda, AWS CloudFormation, Amazon SageMaker, and AWS RoboMaker in turn use other AWS services including Amazon CloudWatch and Amazon CloudWatch Logs\. 

The following table shows AWS services used by AWS DeepRacer, directly or indirectly\.


**AWS Services that AWS DeepRacer uses directly or indirectly**  

| AWS service principal | Comments | 
| --- | --- | 
| [https://aws.amazon.com/ecr/](https://aws.amazon.com/ecr/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 
| [https://aws.amazon.com/cloudformation/](https://aws.amazon.com/cloudformation/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 
| [https://aws.amazon.com/cloudwatch/](https://aws.amazon.com/cloudwatch/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 
| [https://aws.amazon.com/ec2/](https://aws.amazon.com/ec2/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 
| [https://aws.amazon.com/ecr/](https://aws.amazon.com/ecr/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 
| [kinesisvideo](https://aws.amazon.com/kinesis/video-streams/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 
| [https://aws.amazon.com/lambda/](https://aws.amazon.com/lambda/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 
| [https://aws.amazon.com/cloudwatch/](https://aws.amazon.com/cloudwatch/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 
| [https://aws.amazon.com/robomaker/](https://aws.amazon.com/robomaker/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 
| [https://aws.amazon.com/s3/](https://aws.amazon.com/s3/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 
| [https://aws.amazon.com/sagemaker/](https://aws.amazon.com/sagemaker/) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/deepracer-dependent-aws-services.html)  | 

 To use AWS DeepRacer to call these services, you must have appropriate IAM roles with required policies attached to them\. Learn the details about these policies and roles in [Required IAM Roles for AWS DeepRacer to Call Dependent AWS Services](deepracer-understand-required-permissions-and-iam-roles.md)\. 