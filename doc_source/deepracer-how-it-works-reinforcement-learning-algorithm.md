# AWS DeepRacer Training Algorithm<a name="deepracer-how-it-works-reinforcement-learning-algorithm"></a>

 AWS DeepRacer uses the [Proximal Policy Optimization \(PPO\)](https://arxiv.org/abs/1707.06347) algorithm to train the reinforcement learning model\. PPO uses two neural networks during training: a policy network and a value network\. The policy network \(also called actor network\) decides which action to take given an image as input\. The value network \(also called critic network\) estimates the cumulative reward we are likely to get given the image as input\. Only the policy network interacts with the simulator and gets deployed to the real agent, namely an AWS DeepRacer vehicle\. 

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-algo-ppo.png)

Below we explain how the actor and critic work together mathematically\. 

PPO is a derivative of the policy gradient method\. In the most basic form, the policy gradient method trains the agent to move along a track by searching for the optimal policy `π*(a|s; θ*)`\. The optimization aims at maximizing a policy score function `J(θ`\) that can be expressed in terms of the immediate reward `r(s,a)` of taking action \(*`a`*\) in state \(*`s`*\) averaged over the state probability distribution `ρ(s)` and the action probability distribution \(`π(a|s; θ)`\):

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-policy-score-function.png)

The optimal policy, as represented by the optimal policy network weights `θ*`, can be expressed as follows:

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-optimal-policy.png)

The maximization can proceed by following the policy gradient ascent over episodes of training data `(s, a, r)`:

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-policy-gradient-ascent-update.png)

 where `α` is known as the learning rate and `∇θJ(θτ)` is the policy gradient with respect to `θ` evaluated at step `τ`\.

In terms of the total future reward: 

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-total-future-reward.png)

where *γ* is the discount factor ranging between 0 and 1, and τ maps to an *experience* \(*s*τ, *a*τ, *r*τ\) at step τ, and the summation includes experiences in an episode that starts from time *t* = 0 and ends at time *t* = *H* when the agent goes off\-track or reaches to the finish line, the score function becomes the expected total future reward averaged over the policy distribution π across many episodes of experiences:

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-policy-score-function-over-experiences.png)

From this definition of `J(θ)`, the policy weight updates can be expressed as follows:

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-policy-gradient-over-experiences.png)

Here, averaging over π is approximated by sample averaging over *N* of episodes each of which consists of possibly unequal *H* number of experiences\. 

The update rule for a policy network weight then becomes:

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-policy-weight-update-over-experiences.png)

The policy gradient method outlined above is of limited utility in practice, because the score function `R(si,t, ai,t)` has high variance as the agent can take many different paths from a given state\. To get around this, one uses a critic network \(`ϕ`\) to estimate the score function\. To illustrate this, let `Vϕ(s)` the value of the critic network, where *s * describes a state and `ϕ` the value network weights\. To train this value network, the estimated value \(`yi,t`\) of state *`s`* at step *`t`* in episode *`i`* is estimated to be the immediate reward taking action *ai,t* at state *si,t* plus the discounted total future value of the state *s* at the next step `t+1` in the same episode: 

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-estimated-value-network.png)

The loss function for the value network weights is:

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-value-network-loss-function.png)

Using the estimated values, the policy gradient for updating the policy network weights `θ` becomes:

![\[\]](http://docs.aws.amazon.com/deepracer/latest/developerguide/images/deepracer-how-it-works-actor-critic-policy-gradient.png)

This formulation changes the policy network weights such that it encourages actions that give higher rewards than prior estimate and discourages otherwise\. 

Every reinforcement learning algorithm needs to balance between exploration and exploitation\. The agent needs to explore the state and action space to learn which actions lead to high rewards in unexplored state space\. The agent should also exploit by taking the actions that leads to high rewards so that the model converges to a stable solution\. In our algorithm, the policy network outputs the probability of taking each action and during training the action is chosen by sampling from this probability distribution \(e\.g\. an action with probability 0\.5 will be chosen half the time\)\. During evaluation, the agent picks with action with the highest probability\.

In addition to the above actor\-critic framework, PPO uses importance sampling with clipping, adds a [Gauss\-Markov noise](https://en.wikipedia.org/wiki/Ornstein%E2%80%93Uhlenbeck_process) to encourage exploration and uses [generalized advantage estimation](https://arxiv.org/abs/1506.02438)\. To learn more, see the [original paper](https://arxiv.org/pdf/1707.06347.pdf)\.