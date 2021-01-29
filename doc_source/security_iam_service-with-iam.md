# How AWS DeepRacer Works with IAM<a name="security_iam_service-with-iam"></a>

Before you use IAM to manage access to AWS DeepRacer, you should understand what IAM features are available to use with AWS DeepRacer\. To get a high\-level view of how AWS DeepRacer and other AWS services work with IAM, see [AWS Services That Work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html) in the *IAM User Guide*\.

**Topics**
+ [AWS DeepRacer Identity\-Based Policies](#security_iam_service-with-iam-id-based-policies)
+ [AWS DeepRacer Resource\-Based Policies](#security_iam_service-with-iam-resource-based-policies)

## AWS DeepRacer Identity\-Based Policies<a name="security_iam_service-with-iam-id-based-policies"></a>

With IAM identity\-based policies, you can specify allowed or denied actions and resources as well as the conditions under which actions are allowed or denied\. AWS DeepRacer supports specific actions, resources, and condition keys\. To learn about all of the elements that you use in a JSON policy, see [IAM JSON Policy Elements Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html) in the *IAM User Guide*\.

### Actions<a name="security_iam_service-with-iam-id-based-policies-actions"></a>

Administrators can use AWS JSON policies to specify who has access to what\. That is, which **principal** can perform **actions** on what **resources**, and under what **conditions**\.

The `Action` element of a JSON policy describes the actions that you can use to allow or deny access in a policy\. Policy actions usually have the same name as the associated AWS API operation\. There are some exceptions, such as *permission\-only actions* that don't have a matching API operation\. There are also some operations that require multiple actions in a policy\. These additional actions are called *dependent actions*\.

Include actions in a policy to grant permissions to perform the associated operation\.

### Resources<a name="security_iam_service-with-iam-id-based-policies-resources"></a>

AWS DeepRacer does not support specifying resource ARNs in a policy\.

### Condition Keys<a name="security_iam_service-with-iam-id-based-policies-conditionkeys"></a>

AWS DeepRacer does not provide any service\-specific condition keys, but it does support using some global condition keys\. To see all AWS global condition keys, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\. 

## AWS DeepRacer Resource\-Based Policies<a name="security_iam_service-with-iam-resource-based-policies"></a>

AWS DeepRacer does not support resource\-based policies\. To view an example of a detailed resource\-based policy page, see [https://docs.aws.amazon.com/lambda/latest/dg/access-control-resource-based.html](https://docs.aws.amazon.com/lambda/latest/dg/access-control-resource-based.html)\. 