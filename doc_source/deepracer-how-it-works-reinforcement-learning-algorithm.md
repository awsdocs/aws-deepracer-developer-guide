# AWS DeepRacer Training Algorithms<a name="deepracer-how-it-works-reinforcement-learning-algorithm"></a>

**Proximal Policy Optimization \(PPO\) versus Soft Actor Critic \(SAC\)**  
The algorithms SAC and PPO both learn a policy and value function at the same time, but their strategies vary in three notable ways:


| PPO | SAC | 
| --- | --- | 
|  Works in both discrete and continuous action spaces  |  Works in a continuous action space  | 
|  On\-policy  |  Off\-policy  | 
|  Uses entropy regularization  |  Adds entropy to the maximization objective  | 

**Stable vs\. Data Hungry**  
The information learned by the PPO and SAC algorithms' policies while exploring an environment is utilized differently\. PPO uses on\-policy learning which means that it learns its value function from observations made by the current policy exploring the environment\. SAC uses off\-policy learning which means that it can use observations made by previous policies' exploration of the environment\. The trade\-off between off\-policy and on\-policy learning is often stability vs\. data efficiency\. On\-policy algorithms tend to be more stable but data hungry, whereas off\-policy algorithms tend to be the opposite\.

**Exploration vs\. Exploitation**  
Exploration vs\. exploitation is a key challenge in RL\. An algorithm should exploit known information from previous experiences to achieve higher cumulative rewards, but it also needs to explore to gain new experiences that can be used in finding the optimum policy in the future\. As a policy is trained over multiple iterations and learns more about an environment, it becomes more certain about choosing an action for a given observation\. However, if the policy doesn't explore enough, it will likely stick to information already learned even if it's not at an optimum\. The PPO algorithm encourages exploration by using entropy regularization, which prevents agents from converging to local optima\. The SAC algorithm strikes an exceptional balance between exploration and exploitation by adding entropy to its maximization objective\. 

**Entropy**  
In this context, "entropy" is a measure of the uncertainty in the policy, so it can be interpreted as a measure of how confident a policy is at choosing an action for a given state\. A policy with low entropy is very confident at choosing an action, whereas a policy with high entropy is unsure of which action to choose\.

The SAC algorithm's entropy maximization strategy has similar advantages to the PPO algorithms's use of entropy as a regularizer\. Like PPO, it encourages wider exploration and avoids convergence to a bad local optimum by incentivizing the agent to choose an action with higher entropy\. Unlike entropy regulation, entropy maximization has a unique advantage\. It tends to give up on policies that choose unpromising behavior, which is another reason that the SAC algorithm tends to be more data efficient than PPO\.

Tune the amount of entropy in SAC by using the SAC alpha hyperparameter\. The maximum SAC alpha entropy value \(1\.0\) favors exploration\. The minimum value \(0\.0\) recovers the standard RL objective and neutralizes the entropy bonus that incentivizes exploration\. A good SAC alpha value to begin experiementing with is 0\.5\. Tune accordingly as you iterate on your models\.

Try both PPO and SAC algorithms, experiment with their hyperparameters, and explore with them in different action spaces\.