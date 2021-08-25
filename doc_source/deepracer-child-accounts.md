# Create Child Accounts so Multiple Racers Can Race Under a Single AWS Parent Account<a name="deepracer-child-accounts"></a>

If your company doesn’t use a single AWS account per employee, you can create individual child accounts for them within an AWS Organization, so each employee has their own account to train and race with\.

## Prerequisites<a name="child-account-prereqs"></a>

Before you get started make sure you have the following ready:
+ Work with your AWS account team to determine if adding child accounts is best the fit for your company's account structure\.
+ Have [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html) installed on your computer\. Familiarity with AWS CLI is recommended\.
+ Have [jq](https://stedolan.github.io/jq/download/) installed on your computer\.
+ Have [Python](https://www.python.org/downloads/) installed on your computer\.
+ Have the necessary permissions to [create an organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_create.html) with AWS Organizations\. Familiarity with AWS Organizations is recommended\.

In the AWS DeepRacer console, training and racing activities are managed at the AWS account level\. This means that every individual who has access to a specific AWS account will see all AWS DeepRacer models in that account and will share a single racer alias for all race submissions\. In this topic, enterprise customers, whose employees share one account ID using individual IAM roles, can learn to enter multiple racers into virtual AWS DeepRacer community competitions\.
+ If each employee has their own AWS account ID, you do not need to set up child accounts\. Individuals with their own AWS DeepRacer account ID can submit a model to any type of leaderboard\.
+ If all employees share one primary AWS account ID using different IAM roles, all employees share a single leaderboard submission for all leaderboards, including community leaderboards\. Using AWS Organizations and the provided scripts to create individual accounts as a child to the primary account may be the best way to allow multiple employees to submit separate models to a leaderboard at the same time\.
**Important**  
The provided scripts only work with the entity, *IAM role*\. Some enterprise customers set up their accounts using the *IAM user* entity\. For help converting *IAM users* to *IAM roles* contact your AWS account team\.

## Create Child Accounts for a DeepRacer Engagement<a name="child-accounts-procedure"></a>

**To create child accounts**

1. Open a web browser on your computer and navigate to [ChildAccounts\.zip](https://github.com/aws-samples/aws-deepracer-workshops/tree/master/CommunityRaces/ChildAccountsWithAWSOrganizations), which opens a zipped file on GitHub\. Download the file and unzip it to find a folder containing these files:

   1. `templates` \(folder\)

      1. `deepracer_policy_template.json`

      1. `sagemaker_policy_template.json`

      1. `trust_policy_template.json`

   1. `.DS_Store`

   1. `cleanup_sagemaker`

   1. `make_child_accounts.sh`

   1. `update_child_accounts.sh`

1. Edit the trust\_policy\_template\.json file in the templates subdirectory\. You may need to adjust this policy for your environment\. For example, if you're using a Security Assertion Markup Language \(SAML\) provider or another system, add it to the trust policy\.

1. In another tab or window, open [Creating an Organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_create.html), a developer guide topic for AWS Organizations\.

1. If you are using AWS CLI or AWS API, choose the **AWS CLI, AWS API** tab and follow the steps to create an organization\. If you are using the console, follow the steps in *To create an organization*, the tab for which is selected by default\.

1. Next, find steps to create new accounts for your enterprise customer employees for AWS CLI, AWS API, and in the management console in [Creating an AWS account in your organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_accounts_create.html#orgs_manage_accounts_create-new)\. By default, you are limited to four child accounts\. To raise the account limit:

   1. Log into to the AWS Management Console and navigate to [Service Quotas](https://console.aws.amazon.com/servicequotas/#!/services/organizations/quotas)\.

   1. Choose **Default maximum number of accounts**\.

   1. Next, choose **Request quota increase**\.

   1. Enter a number that's a more appropriate limit for the number of accounts you want to create into **Change quota value**\.

   1. Choose **Request**\. Once you've been granted the service quota increase, continue with the rest of the setup steps\.

1. Next, open a CLI terminal window and type the following:

   ```
                       curl "https://aws.amazon.com/deepracer/accounts-v3.zip" -o "deepracer-accounts-v3.zip"
                       unzip deepracer-accounts-v3.zip
                       chmod +x make_child_accounts.sh
                       chmod +x update_child_accounts.sh
                       chmod +x cleanup_maker.sh
   ```

1. Create the following environment variables\. For Linux or Mac, execute the following and ensure you replace the text including the ** with the appropriate values\.

    Setting 'USE\_SAGEMAKER=false' will provide basic read\-only permission to AWS DeepRacer and Amazon Simple Storage Service \(Amazon S3\), and only in us\-east\-1\. Amazon S3 can be removed from the policy template if you don't want users to have the ability to import pre\-existing models\.

   To have your racers [train directly in Amazon Sagemaker](https://aws.amazon.com/blogs/machine-learning/custom-deep-reinforcement-learning-and-multi-track-training-for-aws-deepracer-with-amazon-sagemaker-rl-notebook/), set 'USE\_SAGEMAKER=true'\. This will provide additional permissions to access SageMaker and AWS Robomaker beyond what is provided in the basic policy\.

   ```
                       export NAMED_PROFILE=named profile
                       export NUMBER_OF_CHILD_ACCOUNTS=25
                       export EMAIL_ADDRESS_PREFIX=your email address
                       export ACCOUNT_NAME=your account name
                       export OU_ID=org id
                       export DEEPRACER_ROLE=OrganizationAccountAccessRole
                       export USE_SAGEMAKER=true or false
   ```

1. Once you have exported the environment variables, you're ready to execute one of the following scripts\. If you wish to create new child accounts or add additional child accounts, run the command \. Note: This script creates the appropriate policy, and a role for each child account\. And, if the script did not complete the correct number of child accounts, the export above can be modified, return, and this script will add new child accounts until the count equals 'NUMBER\_OF\_CHILD\_ACCOUNTS'\.

   ```
                       ./make_child_accounts.sh
   ```

1. After creating the desired number of child accounts, move them into the `OU` underneath `root `in the Organizations window of the AWS console\.

1. To update permissions on existing child accounts, run the following command\. It will delete the AWS DeepRacer policy and role and replace them, depending upon the settings above\.

   ```
                       ./update_child_accounts.sh
   ```

### Clean up Amazon Sagemaker Notebooks<a name="child-accounts-clean-up"></a>

**Cleanup**
**Note**  
This cleanup script relies on the region set in the CLI configuration, for example `aws configure`, and will only delete notebooks and jobs for that region\.

1. After your races are complete, if you set 'USE\_SAGEMAKER=true', run the following script to delete all sagemaker notebooks and training jobs\.

   ```
                      ./cleanup_sagemaker.sh
   ```

Multiple enterprise customer employees can now race in virtual AWS DeepRacer community competitions at the same time\.
