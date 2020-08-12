# AWS DeepRacer Reward Function Examples<a name="deepracer-reward-function-examples"></a>

The following lists some examples of the AWS DeepRacer reward function\.

**Topics**
+ [Example 1: Follow the Center Line in Time Trials](#deepracer-reward-function-example-0)
+ [Example 2: Stay Inside the Two Borders in Time Trials](#deepracer-reward-function-example-1)
+ [Example 3: Prevent Zig\-Zag in Time Trials](#deepracer-reward-function-example-2)
+ [Example 4: Stay On One Lane without Crashing into Stationary Obstacles or Moving Vehicles](#deepracer-reward-function-example-3)

## Example 1: Follow the Center Line in Time Trials<a name="deepracer-reward-function-example-0"></a>

 This example determines how far away the agent is from the center line, and gives higher reward if it is closer to the center of the track, encouraging the agent to closely follow the center line\. 

```
def reward_function(params):
    '''
    Example of rewarding the agent to follow center line
    '''
    
    # Read input parameters
    track_width = params['track_width']
    distance_from_center = params['distance_from_center']

    # Calculate 3 markers that are increasingly further away from the center line
    marker_1 = 0.1 * track_width
    marker_2 = 0.25 * track_width
    marker_3 = 0.5 * track_width

    # Give higher reward if the car is closer to center line and vice versa
    if distance_from_center <= marker_1:
        reward = 1
    elif distance_from_center <= marker_2:
        reward = 0.5
    elif distance_from_center <= marker_3:
        reward = 0.1
    else:
        reward = 1e-3  # likely crashed/ close to off track

    return reward
```

## Example 2: Stay Inside the Two Borders in Time Trials<a name="deepracer-reward-function-example-1"></a>

 This example simply gives high rewards if the agent stays inside the borders, and let the agent figure out what is the best path to finish a lap\. It is easy to program and understand, but likely takes longer to converge\. 

```
def reward_function(params):
    '''
    Example of rewarding the agent to stay inside the two borders of the track
    '''
    
    # Read input parameters
    all_wheels_on_track = params['all_wheels_on_track']
    distance_from_center = params['distance_from_center']
    track_width = params['track_width']
    
    # Give a very low reward by default
    reward = 1e-3

    # Give a high reward if no wheels go off the track and 
    # the car is somewhere in between the track borders 
    if all_wheels_on_track and (0.5*track_width - distance_from_center) >= 0.05:
        reward = 1.0

    # Always return a float value
    return reward
```

## Example 3: Prevent Zig\-Zag in Time Trials<a name="deepracer-reward-function-example-2"></a>

 This example incentivizes the agent to follow the center line but penalizes with lower reward if it steers too much, which helps prevent zig\-zag behavior\. The agent learns to drive smoothly in the simulator and likely keeps the same behavior when deployed in the physical vehicle\. 

```
def reward_function(params):
    '''
    Example of penalize steering, which helps mitigate zig-zag behaviors
    '''
    
    # Read input parameters
    distance_from_center = params['distance_from_center']
    track_width = params['track_width']
    steering = abs(params['steering_angle']) # Only need the absolute steering angle

    # Calculate 3 marks that are farther and father away from the center line
    marker_1 = 0.1 * track_width
    marker_2 = 0.25 * track_width
    marker_3 = 0.5 * track_width

    # Give higher reward if the car is closer to center line and vice versa
    if distance_from_center <= marker_1:
        reward = 1.0
    elif distance_from_center <= marker_2:
        reward = 0.5
    elif distance_from_center <= marker_3:
        reward = 0.1
    else:
        reward = 1e-3  # likely crashed/ close to off track

    # Steering penality threshold, change the number based on your action space setting
    ABS_STEERING_THRESHOLD = 15 

    # Penalize reward if the car is steering too much
    if steering > ABS_STEERING_THRESHOLD:
        reward *= 0.8

    return float(reward)
```

## Example 4: Stay On One Lane without Crashing into Stationary Obstacles or Moving Vehicles<a name="deepracer-reward-function-example-3"></a>

This reward function rewards the agent to stay between the track borders and penalizes the agent for getting too close to the next object in the front\. The agent can move from lane to lane to avoid crashes\. The total reward is a weighted sum of the reward and penalty\. The example gives more weight to the penalty term to focus more on safety by avoiding crashes\. You can play with different averaging weights to train the agent with different driving behaviors and to achieve different driving performances\.

```
def reward_function(params):
    '''
    Example of rewarding the agent to stay inside two borders
    and penalizing getting too close to the objects in front
    '''

    all_wheels_on_track = params['all_wheels_on_track']
    distance_from_center = params['distance_from_center']
    track_width = params['track_width']
    objects_distance = params['objects_distance']
    _, next_object_index = params['closest_objects']
    objects_left_of_center = params['objects_left_of_center']
    is_left_of_center = params['is_left_of_center']

    # Initialize reward with a small number but not zero
    # because zero means off-track or crashed
    reward = 1e-3

    # Reward if the agent stays inside the two borders of the track
    if all_wheels_on_track and (0.5 * track_width - distance_from_center) >= 0.05:
        reward_lane = 1.0
    else:
        reward_lane = 1e-3

    # Penalize if the agent is too close to the next object
    reward_avoid = 1.0

    # Distance to the next object
    distance_closest_object = objects_distance[next_object_index]
    # Decide if the agent and the next object is on the same lane
    is_same_lane = objects_left_of_center[next_object_index] == is_left_of_center
    
    if is_same_lane:
        if 0.5 <= distance_closest_object < 0.8: 
            reward_avoid *= 0.5
        elif 0.3 <= distance_closest_object < 0.5:
            reward_avoid *= 0.2
        elif distance_closest_object < 0.3:
            reward_avoid = 1e-3 # Likely crashed

    # Calculate reward by putting different weights on 
    # the two aspects above
    reward += 1.0 * reward_lane + 4.0 * reward_avoid

    return reward
```