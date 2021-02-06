# Add, View, and Edit Tags for a New Resource<a name="tags-new"></a>

Adding tags to a new car, RL model, or community races leaderboard can help you identify, organize, track cost allocation, and manage access to these resources\. Add one or more tags \(key\-value pairs\) to a model or leaderboard\. For each resource, each tag key must be unique, and each tag key can have only one value, but one resource may have up to 50 tags\.

Create and apply the tags one resource at a time in the AWS DeepRacer console or use the [Tag Editor](https://docs.aws.amazon.com/ARG/latest/userguide/tag-editor.html) to add, edit, or delete multiple resources at once\.

**Important**  
Editing tags for an RL model or community races leaderboard can impact access to those resources\. Before you edit the name \(key\) or value of a tag, make sure to review any IAM policies that might use the key or value for a tag to control access to those resources\.

**To Add, View, and Edit Tags for a New RL Model**  
Use the AWS DeepRacer console to add, view, and edit tags to a new RL model\.

1. In **Your models**, choose **Create model**\.

1. On the **Create model** page, after filling out the **Training details**, expand the **Tags** heading\.

1. Under the **Tags** heading, choose **Add new tag**\.

1. In **Key**, enter a name for the tag\. You can add an optional value for the tag in **Value**\. For more information about naming tags, see the Best Practices for Naming Tags and Resources topic in the [Tagging best practices](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf) whitepaper\.

1. \(Optional\) To add another tag, choose **Add new tag** again\.

1. \(Optional\) To remove an individual key or value, select the **X** next to it\.

1. \(Optional\) To remove a key\-value pair, choose **Remove**\.

1. When you have finished adding tags, choose a track under **Environment simulation** and select **Next**\.

After tagging and submitting a new model for training, you can manage its tags during or after training and evaluation under the **Tags** heading at the bottom of the page\.

1. Choose **Manage tags**\.

1. In the **Manage tags** pop up box, you can remove a tag you have created by selecting the **Remove** button next to the tag you want to remove or choose **Add a new tag** to add a new tag\.

1. If you choose to add a new tag, in **Key**, enter a name for the tag\. You can add an optional value for the tag in **Value**\. For more information about naming tags, see the Best Practices for Naming Tags and Resources topic in the [Tagging best practices](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf) whitepaper\.

1. When you have finished removing and adding tags, choose **Submit**\.

**To Add, View, and Edit Tags for a New Community Races Leaderboard**  
Use the AWS DeepRacer console to add, view, and edit tags to a new community races leaderboard\.

1. In **Community races**, choose **Create race**\.

1. On the **Race details** page, expand the **Tags** heading\.

1. Under the **Tags** heading, choose **Add new tag**\.

1. In **Key**, enter a name for the tag\. You can add an optional value for the tag in **Value**\. For more information about naming tags, see the Best Practices for Naming Tags and Resources topic in the [Tagging best practices](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf) whitepaper\.

1. \(Optional\) To add another tag, choose **Add new tag** again\.

1. \(Optional\) To remove an individual key or value, select the **X** next to it\.

1. \(Optional\) To remove a key\-value pair, choose **Remove**\.

1. When you have finished adding tags, choose a track under **Environment simulation** and select **Next**\.