# Tagging<a name="deepracer-tagris"></a>

A tag is a custom attribute label that you or AWS assigns to an AWS resource\. Each AWS tag has two parts:
+ A tag key \(for example, CostCenter, Environment, Project, or Secret\)\. Tag keys are case sensitive\.
+ An optional field known as a tag value\. Omitting the tag value is the same as using an empty string\. Like tag keys, tag values are case sensitive\.

Together these are known as key\-value pairs\.

Tags help you identify and organize your AWS resources\. Many AWS services support tagging, so you can assign the same tag to resources from different services to indicate that the resources are related\. In AWS DeepRacer, the primary resources are RL models and community races leaderboards, so, for example, you can assign the same tag to an AWS DeepRacer model that you assign to an S3 bucket\. For more information about using tags, see the [Tagging best practices](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf) whitepaper\.

You can use the AWS DeepRacer console or the AWS CLI to add, manage, and remove tags for models and community races leaderboards\. In addition to identifying and organizing your models and leaderboards with tags, you can use tags to track cost allocation and in IAM policies to help control who can view and interact with your resources\.

**Tag to Track Cost Allocation**  
Activate model tags for cost allocation tracking by using the Billing and Cost Management console\. Cost Allocation Tags appear on the console after you've enabled Cost Explorer, Budgets, AWS Cost and Usage Reports, or legacy reports\. After you activate one or more of these AWS services, the tagged resources appear on your cost allocation report\. You can then use the tags on your cost allocation report to track your AWS costs\. Only a management account in an organization and single accounts that aren't members of an organization have access to the Cost Allocation Tags manager in the Billing and Cost Management console\. For more information on using tags to track cost allocation see [User\-Defined Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/custom-tags.html)\.

**Tag to Manage Access**  
You can also tag IAM users and roles to manage access to your models and community races leaderboards\. To learn how to tag IAM users and roles, see [Tagging IAM users and roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags.html)\. To view a tutorial for creating and testing a policy that allows IAM roles with principal tags to access resources with matching tags, see [ IAM Tutorial: Define permissions to access AWS resources based on tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_attribute-based-access-control.html)\. For more information on using tags to control access to your AWS resources that support tagging see [Controlling access to AWS resources using resource tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html#access_tags_control-requests)\. 

**Topics**
+ [Add a Tag](add-a-tag.md)
+ [View tags](view-tags.md)
+ [Edit tags](edit-tags.md)
+ [Remove tags](remove-tags.md)