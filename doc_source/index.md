# AWS DeepRacer Developer Guide

-----
*****Copyright &copy; 2019 Amazon Web Services, Inc. and/or its affiliates. All rights reserved.*****

-----
Amazon's trademarks and trade dress may not be used in 
     connection with any product or service that is not Amazon's, 
     in any manner that is likely to cause confusion among customers, 
     or in any manner that disparages or discredits Amazon. All other 
     trademarks not owned by Amazon are the property of their respective
     owners, who may or may not be affiliated with, connected to, or 
     sponsored by Amazon.

-----
## Contents
+ [What Is AWS DeepRacer?](what-is-deepracer.md)
   + [AWS DeepRacer As an Integrated Learning System](deepracer-is-a-learning-environment-for-reinforcement-learning.md)
   + [AWS DeepRacer Basic Concepts and Terminology](deepracer-basic-concept.md)
+ [How AWS DeepRacer Works](deepracer-how-it-works.md)
   + [Overview of Reinforcement Learning](deepracer-how-it-works-overview-reinforcement-learning.md)
   + [AWS DeepRacer Action Space and Reward Function](deepracer-how-it-works-action-space.md)
   + [AWS DeepRacer Training Algorithm](deepracer-how-it-works-reinforcement-learning-algorithm.md)
   + [AWS DeepRacer Service Architecture](deepracer-how-it-works-service-architecture.md)
   + [AWS DeepRacer Solution Workflow](deepracer-how-it-works-solution-workflow.md)
   + [Simulated-to-Real Performance Gaps](deepracer-how-it-works-virtual-to-physical.md)
+ [Get Started with AWS DeepRacer](deepracer-get-started.md)
   + [Set Up for Using AWS DeepRacer](deepracer-setup.md)
      + [Sign Up Your AWS Account](deepracer-sign-up-aws-account.md)
      + [Create an IAM User](deepracer-create-iam-user.md)
      + [AWS DeepRacer-Dependent AWS Services](deepracer-dependent-aws-services.md)
      + [Required IAM Roles for AWS DeepRacer to Call Dependent AWS Services](deepracer-understand-required-permissions-and-iam-roles.md)
   + [Train Your First AWS DeepRacer Model for Autonomous Racing](deepracer-get-started-training-model.md)
   + [Evaluate Your AWS DeepRacer Models in Simulation](deepracer-get-started-test-in-simulator.md)
+ [Train and Evaluate AWS DeepRacer Models](create-deepracer-project.md)
   + [Train and Evaluate AWS DeepRacer Models Using the AWS DeepRacer Console](deepracer-console-train-evaluate-models.md)
   + [Train and Evaluate AWS DeepRacer Models Using Amazon SageMaker Notebooks](train-evaluate-models-using-sagemaker-notebook.md)
   + [Input Parameters of the AWS DeepRacer Reward Function](deepracer-reward-function-input.md)
+ [Operate Your AWS DeepRacer Vehicle](operate-deepracer-vehicle.md)
   + [Get to Know Your AWS DeepRacer Vehicle](deepracer-prep-vehicle.md)
      + [AWS DeepRacer Vehicle LED Indicators](deepracer-vehicle-led-indicators.md)
      + [AWS DeepLens Vehicle Chassis Parts](deepracer-vehicle-chassis-parts.md)
   + [Choose a Wi-Fi Network for Your AWS DeepRacer Vehicle](deepracer-set-up-vehicle.md)
   + [Launch AWS DeepRacer Vehicle's Device Console](deepracer-set-up-vehicle-test-drive.md)
   + [Calibrate Your AWS DeepRacer Vehicle](deepracer-calibrate-vehicle.md)
   + [Upload a Model to Your AWS DeepRacer Vehicle](deepracer-upload-model-to-vehicle.md)
   + [Drive Your AWS DeepRacer Vehicle](deepracer-drive-your-vehicle.md)
   + [Inspect and Manage Your AWS DeepRacer Vehicle Settings](deepracer-manage-vehicle-settings.md)
   + [View Your AWS DeepRacer Vehicle Logs](deepracer-drive-vehicle-logs.md)
+ [Build Your Physical Track for AWS DeepRacer](deepracer-build-your-track.md)
   + [Track Materials and Build Tools](deepracer-build-your-track-materials-and-tools.md)
   + [Lay Your Track for AWS DeepRacer](deepracer-build-your-track-construction.md)
   + [AWS DeepRacer Track Design Templates](deepracer-track-examples.md)
+ [Rank AWS DeepRacer Models in Leaderboard](deepracer-racing-series.md)
   + [Submit Your Model to an AWS DeepRacer Leaderboard](deepracer-submit-model-to-leaderboard.md)
+ [Troubleshoot Common AWS DeepRacer Issues](deepracer-troubleshooting.md)
   + [How to Switch AWS DeepRacer Compute Module Power Source from Battery to Power Outlet?](deepracer-troubleshooting-switch-battery-to-wall-power.md)
   + [How to Connect Your AWS DeepRacer to Your Wi-Fi Network?](deepracer-troubleshooting-wifi-connection-first-time.md)
   + [How to Charge the AWS DeepRacer Drive Module Battery?](deepracer-troubleshooting-charge-vehicle-battery-first-time.md)
   + [How to Charge the AWS DeepRacer Compute Module Battery?](deepracer-troubleshooting-charge-compute-battery.md)
   + [How to Maintain Vehicle's Wi-Fi Connection?](deepracer-troubleshooting-maintain-vehicle-connection.md)
   + [How to Get the MAC Address of Your AWS DeepRacer Device?](deepracer-troubleshooting-get-mac-address.md)
   + [How to Recover Your AWS DeepRacer Device Console Default Password?](deepracer-troubleshooting-recover-device-web-server-password.md)
   + [How to Manually Update Your AWS DeepRacer Device?](deepracer-troubleshooting-manual-update-device.md)
   + [Why Can't I Connect to the Device Console with USB Connection between My Computer and Vehicle?](deepracer-troubleshooting-connect-to-deepracer.aws.md)
   + [How to Diagnose and Resolve Common AWS DeepRacer Operational Issues?](deepracer-troubleshooting-device-operation-issues.md)
   + [How to Restore Your AWS DeepRacer Vehicle to Factory Settings?](deepracer-troubleshooting-factory-reset.md)
      + [Prepare for Factory Reset to Your AWS DeepRacer Vehicle](deepracer-vehicle-factory-reset-preparation.md)
      + [Restore Your AWS DeepRacer Vehicle to Factory Settings](deepracer-vehicle-factory-reset-instructions.md)
+ [Document History for AWS DeepRacer Developer Guide](doc-history.md)
+ [AWS Glossary](glossary.md)