# A sensitivity formula for risk-sensitive cost and the actor–critic algorithm


Author: V.S. Borkar


## Preface

Actor Critic

Actor-critic is a popular reinforcement learning algorithm that combines elements of both value-based and policy-based methods. The algorithm learns both a policy function (actor) and a value function (critic) to improve decision-making in a given environment.

In actor-critic, the actor represents the policy function, which maps states to actions. The goal of the actor is to learn a policy that maximizes the expected reward over time. The critic, on the other hand, represents the value function, which estimates the expected cumulative reward for a given state or state-action pair. The critic helps the actor by providing feedback on the quality of the policy.

The actor and critic are trained iteratively. During each iteration, the actor uses the current policy to select an action, and the critic evaluates the state-action value function for that action. The difference between the actual and estimated values is used to update both the actor and the critic. The actor is updated to increase the probability of selecting the action in the current state, and the critic is updated to reduce the error between the estimated and actual values.

The actor-critic algorithm has several advantages over other reinforcement learning methods. For example, it can handle continuous action spaces and high-dimensional state spaces, which can be challenging for value-based methods. Additionally, it can learn quickly and efficiently from experience, making it a popular choice for many real-world applications.



## 1. Introduction

* Our aim here is to propose and analyse an actor–critic algorithm for risk-sensitive control
* inspired by the policy iteration algorithm for risksensitive control

## 2. Dynamic programming for risk-sensitive control
* Consider a controlled Markov chain Xn; n>= 0; on a **finite** state space S, with a **finite** action space A
* $\sum_j p(i, u, j)=1, \quad i \in S, u \in A$
* P : transitiion probabilites , initial_state X action X new_state
* 
* 
* 
* 
* 
