# Add, View, and Edit Tags for an Existing Resource<a name="tags-exisiting"></a>

Adding tags to an existing AWS DeepRacer RL model or community races leaderboard can help you identify, organize, track cost allocation, and manage access to these resources\. Add one or more tags \(key\-value pairs\) to a model or leaderboard\. For each resource, each tag key must be unique, and each tag key can have only one value, but one resource may have up to 50 tags\.

Create and apply the tags one resource at a time in the AWS DeepRacer console or use the [Tag Editor](https://docs.aws.amazon.com/ARG/latest/userguide/tag-editor.html) to add, edit, or delete multiple resources at once\.

**Important**  
Editing tags for an RL model or community races leaderboard can impact access to those resources\. Before you edit the name \(key\) or value of a tag, make sure to review any IAM policies that might use the key or value for a tag to control access to those resources\.

**To Add, View, and Edit Tags for an Existing RL Model**  
You can use the AWS DeepRacer console to add, view, or edit tags for an existing RL model\.

1. In **Your models**, select a model from the list by choosing its name\.

1. Select **Actions**\.

1. Choose **Manage tags** from the drop down list\.

1. In the **Manage tags** pop up box, you can view, add, or remove a tags:

   1. To add a tag, choose **Add new tag**\. In **Key**, enter a name for the tag\. You can add an optional value for the tag in **Value**\. For more information about naming tags, see the Best Practices for Naming Tags and Resources topic in the [Tagging best practices](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf) whitepaper\.

   1. To add another tag, choose **Add new tag** again\.

   1. To remove an individual key or value, select the **X** next to it\.

   1. To remove a key\-value pair, choose **Remove**\.

1. When you have finished viewing, adding, and removing tags, choose **Submit**\.

**To Add, View, and Edit Tags for an Existing Community Races Leaderboard**

1. In **Community races**, choose **Manage races**\.

1. On the **Manage races** page, select a race\.

1. Select **Actions**\.

1. Choose **Manage tags** from the drop down list\.

1. In the **Manage tags** pop up box, you can view, add, or remove a tags:

   1. To add a tag, choose **Add new tag**\. In **Key**, enter a name for the tag\. You can add an optional value for the tag in **Value**\. For more information about naming tags, see the Best Practices for Naming Tags and Resources topic in the [Tagging best practices](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf) whitepaper\.

   1. To add another tag, choose **Add new tag** again\.

   1. To remove an individual key or value, select the **X** next to it\.

   1. To remove a key\-value pair, choose **Remove**\.

1. When you have finished viewing, adding, and removing tags, choose **Submit**\.