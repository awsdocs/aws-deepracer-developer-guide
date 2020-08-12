# AWS DeepRacer Track Design Templates<a name="deepracer-track-examples"></a>

The following track design templates show AWS DeepRacer tracks that you can build by following the [instructions](deepracer-build-your-track-construction.md) presented in this section\.

**Topics**
+ [AWS DeepRacer Single\-Turn Track Template](#deepracer-track-example-single-turn)
+ [AWS DeepRacer S\-Curve Track Template](#deepracer-track-example-s-curve)
+ [AWS DeepRacer Loop Track Template](#deepracer-track-example-loop)
+ [AWS DeepRacer AWS re:Invent 2018 Track Template](#deepracer-track-example-reinvent-2018)
+ [AWS DeepRacer Championship Cup 2019 Track Template](#deepracer-track-example-reinvent-2019)

## AWS DeepRacer Single\-Turn Track Template<a name="deepracer-track-example-single-turn"></a>

This basic track template consists of two straight track segments connected by a curved track segment\. Models trained with this track should make your AWS DeepRacer vehicle drive in straight line or to make turns in one direction\.

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-track-example-single-turn.png)

## AWS DeepRacer S\-Curve Track Template<a name="deepracer-track-example-s-curve"></a>

The track is more complex than the single\-turn track because the model needs to learn to make turns in two directions\. You can easily extend the single\-turn track construction instructions to this track by turning it in the opposite direction after the first turn\.

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-track-example-s-curve.png)

## AWS DeepRacer Loop Track Template<a name="deepracer-track-example-loop"></a>

This regular loop track is a repeating, 90\-degree, single\-turn track\. Obviously, it requires a larger enclosing area for laying the entire track\.

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-track-example-loop.png)

## AWS DeepRacer AWS re:Invent 2018 Track Template<a name="deepracer-track-example-reinvent-2018"></a>

This less regular loop track was first presented at the AWS re:Invent 2018\. Models trained on this track must learn how to turn left and right at various angles and how to move straight ahead in various directions\.

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-track-guideline.png)

At AWS re:Invent 2018, the track size measured 26 feet long by 17 feet wide\. To change the scale, be aware that the scaled\-down track may become too narrow to fit the model trained on a wider track\.

To reproduce the same color production, use the following color specifications: 
+ Green: PMS 3395C
+ Orange: PMS 137C
+ Black: PMS 432C
+ White: CMYK 0\-0\-2\-9

This track was tested with the following materials for its surface:
+ Carpet

   The track was printed on 8\-ounce, dye\-sublimated, polyester\-faced carpet with latex rubberized backing\. Carpet is durable, provides great performance, but is expensive\.
+ Vinyl

  The track was printed on 13\-ounce scrim vinyl with a matte finish to reduce glare\. Vinyl is typically cheaper than carpet and provides good performance\. Vinyl is not as durable as carpet\.

 Due to its large size, the track cannot be easily printed on a single piece of material\. Align track lines well when connecting pieces together\.

For more detailed information, see [the AWS DeepRacer re:Invent 2018 track specification](samples/deepracer_track_reInvent_2018.zip)\. 

## AWS DeepRacer Championship Cup 2019 Track Template<a name="deepracer-track-example-reinvent-2019"></a>

This track was used during the AWS DeepRacer 2019 Championship Cup finals\. It's intended to train models for head\-to\-head racing\.

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-Championship_Cup_2019.png)

The track is 34 feet long and 27 feet wide\. Please see dimensions in the track files below\.

To print or create your own Championship Cup track, download the [AWS DeepRacer Championship Cup 2019 track files here](samples/Championship_Cup_2019_Track.zip)\. 