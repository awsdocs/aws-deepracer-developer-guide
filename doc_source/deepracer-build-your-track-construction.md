# Lay Your Track for AWS DeepRacer<a name="deepracer-build-your-track-construction"></a>

When you build your track, it's a good practice to start with a simple design, such as a straight or single\-turn track\. Next you can move on to looped tracks\. Here, we use a single\-turn track as an example to walk you through the steps to construct your own track\. First let's review dimensional requirements of a track\.

**Topics**
+ [Dimensional Requirements](#deepracer-build-your-track-construction-dimensions)
+ [Considerations for Model Performance](#deepracer-build-your-track-performance-considerations)
+ [Steps to Build the Track](#deepracer-build-your-track-construction-steps)

## Dimensional Requirements<a name="deepracer-build-your-track-construction-dimensions"></a>

You can build a track of any shape as long as it meets the following requirements:
+ **Minimum turning radius**: 

  On a curved track, the turning radius \(`r`\) measures from the circle center to the outside border, as illustrated below\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-track-turning-radius.png)

  The minimum turning radius \(`rmin`\) depends on the track turning angle \(α\) at a corner and should comply to the following limits:
  + If the track's turning angle is `α ≤ 90 degrees`, 

    `rmin ≥ 25 inches` 

    We recommend 30 inches\. 
  + If the track's turning angle is `α > 90 degrees`, α

    `rmin ≥ 30 inches`\.

    We recommend 35 inches\. 
+ **Track width**, 

  The track width \(`wtrack`\) should comply to the following limit:

  `wtrack ≥ 24 ± 3 inches`\. 
+ **Track surface**: 

  The track surface should be smooth and of a uniform dark color\. The minimum enclosing area should be `30 inches x 60 inches` in size\. 

  Carpeted and wood floors work well\. [Interlocked foam or rubber pads](https://www.amazon.com/AmazonBasics-Exercise-Foam-Interlocking-Tiles/dp/B0719B8HQZ/ref=sr_1_4_acs_sk_pb_2_sl?s=exercise-and-fitness&ie=UTF8&qid=1549400888&sr=1-4-acs&keywords=rubber+tiles) match the simulated environment better than wood, but this is not required\. Concrete floors can be problematic due to light reflection on the surface\.
+ **Track barrier**

  Though not required, we recommended that you encircle the track with uniform\-colored barriers that are at least 2\.5 feet tall and 2 feet away from the track at all points\.

## Considerations for Model Performance<a name="deepracer-build-your-track-performance-considerations"></a>

How you build a track can affect the reliability and performance of a trained model\. The following are factors you should consider when building your own tracks\.

1. Do not place any white objects on or near your track\. If necessary, remove any white object from the track or its vicinity\. This is because training in the simulated environment assumes that only the track borders are white\.

1.  Use clean and continuous tape to mark the track borders\. Broken or creased track borders can affect the trained model performance\.

1. Avoid using a reflective surface as the track floor\. Reduce glare from bright lights\. The glare from straight edges can be misinterpreted as objects or borders\.

1. Do not use a track floor with line markings other than the track lines\. The model might interpret the non\-track lines as part of the track\.

1. Place barriers around the track to help reduce distractions from background objects\.

## Steps to Build the Track<a name="deepracer-build-your-track-construction-steps"></a>

As an illustration, we use the most basic single\-turn track\. You can modify the instructions to create a more complex track such as an S\-curve, a loop, or the AWS re:invent 2018 track\. 

**To build an AWS DeepRacer single\-turn track**

1. To construct the straight portion of the track, follow the steps below and refer to the diagram\.

   1. Put a 60\-inch long piece of tape on the floor to lay down the first border in a straight line \(`1`\)\.

   1. Use a tape measure to locate the second border's two end points, \(`2`\) and \(`3`\)\. Put them 24 inches apart from the first border's two ends\.

   1. Put another 60\-inch long piece of tape on the floor to lay down the second boarder to connect the two endpoints \(`2`\) and \(`3`\)\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-track-example-straight-60inches.png)

   We assume the straight track segment is 60\-inches long and 24\-inches wide\. You can adjust the length and width to fit to your space, provided that the dimensional requirements are met\. 

1.  To make the track to turn at a 60\-degree angle, do the following and refer to the diagram:

   1. Use the tape measure to locate the center \(`4`\) of the turning radius \(`4-3` or `4-6`\)\. Mark the center with a piece of tape\.

   1. Draw an equilateral triangle\. The three sides are \(`3-4`\), \(`4-6`\), and \(`6-3`\)\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-track-example-triangle-60degrees.png)

      To make a 60\-degree turn along the track, use the equilateral triangle \(`3-4-6`\) to determine the locations of the two final end points \(`5`\) and \(`6`\) for the curved track segment\. For turns at a different angle, you can use a protractor \(or a protractor app\) to locate the two final ends \(`5`\) and \(`6`\) of the curved track segment\. Turning radius variations are acceptable as long as the minimum turning radius requirement in Step 2 is met\.

   1. Put small tape segments, e\.g\. 4\-inches each, on the floor to lay the curved border segments \(`7`\) and \(`8`\) and connect them with the straight\-line borders\. The two curved borders don't need to be parallel\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-track-example-curved-60degrees.png)

1.  To extend the track with the next straight segment of 30 inches long and 24 inches wide, do the following:

   1.  Put a 30\-inch long piece of tape on the floor to lay down the first border \(4\-8\) perpendicular to the edge \(3\-5\)\.   
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-track-example-straight-border-after-curve.png)

   1. Use the tape measure to locate the ending point of the second border \(9\)\. You can customize the length of the straight lines to fit to the space you have\. 

   1.  Put another 30\-inch long piece of tape on the floor to lay down the second border \(5\-9\) perpendicular to the edge \(3\-5\)\.  
![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-track-example-straight-segment-after-curve.png)

   We assume the second straight track segment is 30 inches long and 24 inches wide\. You can adjust the length and width to fit to your space, provided that the dimensional requirements are met and the dimensions are consistent with other track segments\. 

1. Optionally, cut tape segments of 4 inches long and then place the tape segments 2 inches apart along the track center to lay the dashed center line\.

You've now finished building the single\-turn track\. To help your vehicle to better distinguish the drivable surfaces from non\-drivable surfaces, you should paint the off\-track surface a color of sufficient contrast with respect to the on\-track surface color\. To ensure safety, you could encircle the track with uniform\-colored barriers that are at least 2\.5 feet tall and 2 feet away from the track at all points\. 

You can apply the instructions to extend the track to [more complex shapes](deepracer-track-examples.md)\.