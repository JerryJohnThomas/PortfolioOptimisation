# 


## what are we trying to do ???

* DDPG makes discrete continous , similary do something for baoker paper
* 
* 
* 


##  Understanding DDPG 

### Attempt 0 

![ref](https://towardsdatascience.com/deep-deterministic-policy-gradient-ddpg-theory-and-implementation-747a3010e82f)
* DQN
    * In DQN the optimal action is taken by taking argmax over the Q-values of all actions
    * In DDPG the actor is a policy network that does exactly this. It outputs the action directly (action can be continuous), bypassing the argmax
    * **DQN thing can be done only for finite/discreted action space**
    * **DDPG by passes this**
* Models
    * The policy is deterministic since it directly **outputs the action**
* together working
    * ![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*sYVh6sZWNXED2x21UjUAeA.png)
* Loss Functions
    * The loss function for Critic (Q) and Actor (mu)
    * ![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*hbUTglEaVdHliFDKv3OOhQ.png)
    * 
* Actor Loss
    * The loss is simply the sum of Q-values for the states
    * For computing the Q values we use the Critic network and pass the action computed by the Actor-network
* To increase stability during training we include target critic and actor networks to calculate Q-value for next state in TD-error computations.
*  In DDPG we perform a “soft update” where only a fraction of main weights are transferred in the following manner,
* ![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*rFLzMuvSYUmNWGLIxuHvrg.png)
* Tau is a parameter that is typically chosen to be close to 1 (eg. 0.999)
* COde 
```python

## Initialisation
# We initialize 4-networks: The main Actor and Critic and the target Actor and Critic

X_shape = (num_states)
QA_shape = (num_states + num_actions)
hidden_sizes_1=(1000,500,200)
hidden_sizes_2=(400,200)

# Main network outputs
mu = ANN2(X_shape,list(hidden_sizes_1)+[num_actions], hidden_activation='relu', output_activation='tanh')
q_mu = ANN2(QA_shape, list(hidden_sizes_2)+[1], hidden_activation='relu')

# Target networks
mu_target = ANN2(X_shape,list(hidden_sizes_1)+[num_actions], hidden_activation='relu', output_activation='tanh')
q_mu_target = ANN2(QA_shape, list(hidden_sizes_2)+[1], hidden_activation='relu')

# target is the best thing we are hoping for
```

```python
## Training
X,A,R,X2,D = replay_buffer.sample(batch_size)

#Actor optimization   
with tf.GradientTape() as tape2:
  Aprime = action_max * mu.predict_on_batch(X)
  temp = tf.keras.layers.concatenate([Xten,Aprime],axis=1)
  Q = q_mu.predict_on_batch(temp)
  mu_loss =  -tf.reduce_mean(Q)
  grads_mu = tape2.gradient(mu_loss,mu.trainable_variables)

mu_losses.append(mu_loss)
mu_optimizer.apply_gradients(zip(grads_mu, mu.trainable_variables))



#Critic Optimization
with tf.GradientTape() as tape:
  next_a = action_max * mu_target.predict_on_batch(X2)
  temp = np.concatenate((X2,next_a),axis=1)
  q_target = R + gamma * (1 - D) * q_mu_target.predict_on_batch(temp)
  temp2 = np.concatenate((X,A),axis=1)
  qvals = q_mu.predict_on_batch(temp2) 
  q_loss = tf.reduce_mean((qvals - q_target)**2)
  grads_q = tape.gradient(q_loss,q_mu.trainable_variables)
q_optimizer.apply_gradients(zip(grads_q, q_mu.trainable_variables))
q_losses.append(q_loss)

```

```python

## Model Updates
temp1 = np.array(q_mu_target.get_weights())
temp2 = np.array(q_mu.get_weights())
temp3 = decay*temp1 + (1-decay)*temp2
q_mu_target.set_weights(temp3)

# updating Actor network
temp1 = np.array(mu_target.get_weights())
temp2 = np.array(mu.get_weights())
temp3 = decay*temp1 + (1-decay)*temp2
mu_target.set_weights(temp3)
```

* 
* 
* 



### Attempt 2 (chat gpt) 

#### critic
* critic network that estimates the Q-value (expected future rewards) of a given state-action pair
* This critic network is trained using the Bellman equation, which updates the Q-value estimate based on the observed reward and the expected future reward

#### policy net
* maintains a policy network that learns to maximize the expected future reward
* The policy network is updated using the gradients of the Q-values with respect to the actions, which are estimated using the critic network.

#### innovations

* The key innovation of DDPG is the use of a replay buffer to store experience tuples, which are randomly sampled during training. This allows the algorithm to learn from past experiences and improve its performance. 

#### Losses
* 
* 
* 
* 
* 
* 
* 


### Attempt 3 

[open AI](https://spinningup.openai.com/en/latest/algorithms/ddpg.html)


#### Introduction
* 2 parts of DDPG: learning a Q function, and learning a policy.


#### The Q-Learning Side of DDPG
* First, let’s recap the Bellman equation describing the optimal action-value function, Q^*(s,a). It’s given by
* optimal Q*
* ![](https://spinningup.openai.com/en/latest/_images/math/3a8b6ce0d6c0b68744b5724403f5d70ed5cda5db.svg)
* now approximator $Q_{\phi}(s,a)$
* Loss = how close we are , further the worser
* ![](https://spinningup.openai.com/en/latest/_images/math/31dda6ac0678255c4e192dd6fae4f7ed3c7cd91b.svg)
* Q-learning algorithms for function approximators, such as DQN (and all its variants) and DDPG, are largely based on minimizing this MSBE loss function
* There are two main tricks employed by all of them which are worth describing, and then a specific detail for DDPG.
* Trick One: Replay Buffers.
    * All standard algorithms for training a deep neural network to approximate Q^*(s,a) make use of an experience replay buffer. 
* Trick Two: Target Networks.
    * because when we minimize the MSBE loss, we are trying to make the Q-function be more like this target
    * 
    * 

#### DDPG Detail: Calculating the Max Over Actions in the Target.
* As mentioned earlier: computing the maximum over actions in the target is a challenge in continuous action spaces
* **DDPG deals with this by using a target policy network to compute an action which approximately maximizes $Q_{\phi_{\text{targ}}}.$**
* The target policy network is found the same way as the target Q-function: by polyak averaging the policy parameters over the course of training
* ![](https://spinningup.openai.com/en/latest/_images/math/4421120861d55302d76c7e2fd7cc5b2da7aea320.svg)
* basically max a' Q(s',a') is now replaced by the output of the policy network **where $\mu_{\theta_{\text{targ}}}$ is the target policy.**

#### The Policy Learning Side of DDPG
*  We want to learn a deterministic policy $\mu_{\theta}(s)$ which gives the action that maximizes $Q_{\phi}(s,a)$
* aim: ![](https://spinningup.openai.com/en/latest/_images/math/cc4e3565d839e63e871a1cf7e3ce5e95bb616b29.svg)

#### Exploration vs. Exploitation
* DDPG trains a deterministic policy in an off-policy way
* WHy not on policy?
    * not much exploration
    * Because the policy is deterministic, if the agent were to explore on-policy, in the beginning it would probably not try a wide enough variety of actions to find useful learning signals

#### Code
* 
* ![](https://spinningup.openai.com/en/latest/_images/math/5811066e89799e65be299ec407846103fcf1f746.svg)
* 
* 



