# Lecture 3

Dynamic Programming 
## links
* [video](https://www.youtube.com/watch?v=Nd1-UUMVfz4&list=PLqYmG7hTraZBiG_XpjnPrSNw-1XQaM_gB&index=5)
* [slides](https://www.davidsilver.uk/wp-content/uploads/2020/03/DP.pdf)

## Introduction
* Dynamic Programming requirements
    * Optimal substructure - Optimal solution can be decomposed into subproblems
    * Overlapping subproblems - Subproblems recur many times (hence caching)
* Bellman equation **satisfies both**
    * recursive decomposition
    * value function is the overlapping part. Anything from that state we dont need to re calculate we can use value function
* Planning in MDP 
    * prediction: 
    * control: the best output

## Policy Evaluation
* input: MDP and policy
* output: evaluate a policy 
* we use bellman expectation
* synchronous backups
    * At each iteration k + 1
    * For all states Update $v_{k+1}(s)$ from $v_k(s')$
    * where s' is a successor of s
* This will converge

### example
* we evaluate one policy 
* and we converge to the final v
* $\mathbf{v}^{k+1}=\mathcal{R}^\pi+\gamma \mathcal{P}^\pi \mathbf{v}^k$
* the right side gives us the policy from V.
* policy is like go the best V possible  from every state
* NOTE: we use random policy, without feedback.
![](./assets/l3_p1.png)

## Policy iteration 
* it seems lhs is evaluation and rhs is greedy (both together is policy iteration)
* for above example
    * Given any random policy $\pi$
    * evaluate it i.e the LHS
    * once it converges, compute the RHS policy and that will be the optimal policy 
    * in above example we need to compute RHS only once after the LHS converges 
* but its not always like that.
* ![](./assets/l3_p2.png)
* No matter where you start (value function or policy) we will arrive at the optimal policy 

More mathematics  

* Consider a deterministic policy $a =\pi (s)$ 
$$
\pi^{\prime}(s)=\underset{a \in \mathcal{A}}{\operatorname{argmax}} q_\pi(s, a)
$$
- This improves the value from any state $s$ over one step, **Greedy works**
$$
q_\pi\left(s, \pi^{\prime}(s)\right)=\max _{a \in \mathcal{A}} q_\pi(s, a) \geq q_\pi(s, \pi(s))=v_\pi(s)
$$
It therefore improves the value function, $v_{\pi^{\prime}}(s) \geq v_\pi(s)$
$$
\begin{aligned}
v_\pi(s) & \leq q_\pi\left(s, \pi^{\prime}(s)\right)=\mathbb{E}_{\pi^{\prime}}\left[R_{t+1}+\gamma v_\pi\left(S_{t+1}\right) \mid S_t=s\right] \\
& \leq \mathbb{E}_{\pi^{\prime}}\left[R_{t+1}+\gamma q_\pi\left(S_{t+1}, \pi^{\prime}\left(S_{t+1}\right)\right) \mid S_t=s\right] \\
& \leq \mathbb{E}_{\pi^{\prime}}\left[R_{t+1}+\gamma R_{t+2}+\gamma^2 q_\pi\left(S_{t+2}, \pi^{\prime}\left(S_{t+2}\right)\right) \mid S_t=s\right] \\
& \leq \mathbb{E}_{\pi^{\prime}}\left[R_{t+1}+\gamma R_{t+2}+\ldots \mid S_t=s\right]=v_{\pi^{\prime}}(s)
\end{aligned}
$$
* basically the new policy is better even for 1 step and eventually it will converge
* when it stops then optimal is reached 
>>main take away
* so **policy iteration with greedy solves MDP**
* 56:00
## Till when do we have to iterate
* opt1: changes are less than $\epsilon$ 
* opt2: simply stop after k iterations
    * this seems like magic (no proof here though) 

## Value iteration
### optimatlity
![](./assets/l3_p3.png)
* any state we go to from there everything is optimal 

### finding v*
* given v*(child_state)
* how to find v
![](./assets/l3_p4.png)
* hence given the last v* give it some value, we can calculate everything 1 step behind then 2 steps behing then 3 steps behind 
* work backwards with MDP

### toy example
![](./assets/l3_p5.png)
* here in k iteration we update till k layers of MDP from the goal
* in DP **we update every cell** coz we dont know which layer might take us to the goal
* at each point we try to make the value function as the best thing it can take

### DEMO
* https://www.cs.ubc.ca/~poole/demos/mdp/vi.html

## Summary of DP
* prediction : evaluation
* control: get the optimal/best stuff
![](./assets/l3_p6.png)
* for m actions and n states
    * complexity for stuff based on state-value function $v_\pi(s)$ has $O(m.n^2)$
    * complexity for stuff based on action-value function $q_*(s,a)$ has $O(m^2.n^2)$

## Extensions to DP
* async dp
    * in place dp - 
    * prioritised sweeping - 
    * Real-time dynamic programming - dont update all the states, just the states that the agent visits in real time. use real time samples

* Im not paying much attention from this point
* 
* 
* 





































## Major Takeaways
* In value iteration
    * someone is telling us the dynamic of the system then we are using one V function to find all the other V iteratively
    * we are not solving the RL problem
* In policy iteration
    * we evaluate then greedily select one then repeat
* solve a known MDP