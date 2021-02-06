# Tagging<a name="deepracer-tagging"></a>

A tag is a custom attribute label that you or AWS assigns to an AWS resource\. Each AWS tag has two parts:
+ A tag key \(for example, `companyname`, `costcenter`, `environment`, `project`, or `secret`\)\. Tag keys are case sensitive\.
+ An optional field known as a tag value\. Omitting the tag value is the same as using an empty string\. Like tag keys, tag values are case sensitive\.

Together these are known as key\-value pairs\.

In the AWS DeepRacer service, you can assign tags to cars, RL models, and community races leaderboards\. Tag these and other AWS resources that support tagging to indicate that the resources are related\.In addition to identifying and organizing your models and leaderboards with tags, you can also use tags to track cost allocation and in IAM policies to help control who can view and interact with your resources\. Use the AWS DeepRacer console or the AWS CLI to add, manage, and remove tags\.

 For more information about using tags, see the [Tagging best practices](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf) whitepaper\.

**Tag to Track Cost Allocation**  
AWS Cost Explorer and Cost and Usage Report support the ability to break down AWS costs by tag\. Business tags such as `cost center`, `businessunit`, or `project` can be used to associate AWS costs with an organization’s typical financial reporting categories\. However, a cost allocation report can include any tag allowing you to easily associate costs with technical or security categories, such as specific applications, environments, or compliance programs\. Only a management account in an organization and single accounts that aren't members of an organization have access to the Cost Allocation Tags manager in the Billing and Cost Management console\. For more information on using tags to track cost allocation see [User\-Defined Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/custom-tags.html)\.

**Tag to Manage Access**  
You can also tag IAM users and roles to manage access to your models and community races leaderboards\. To learn how to tag IAM users and roles, see [Tagging IAM users and roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags.html)\. To view a tutorial for creating and testing a policy that allows IAM roles with principal tags to access resources with matching tags, see [ IAM Tutorial: Define permissions to access AWS resources based on tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_attribute-based-access-control.html)\. For more information on using tags to control access to your AWS resources that support tagging see [Controlling access to AWS resources using resource tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html#access_tags_control-requests)\. 

**Topics**
+ [Add, View, and Edit Tags for a New Resource](tags-new.md)
+ [Add, View, and Edit Tags for an Existing Resource](tags-exisiting.md)