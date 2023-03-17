# SARSA 

[ref here](https://colab.research.google.com/github/yfletberliac/rlss-2019/blob/master/labs/solutions/RL.DP%2BQLearning%2BSARSA_solution.ipynb)


#####  Q-learning

The Q-Learning algorithm allows us to estimate the optimal Q function using only trajectories from the MDP obtained by following some exploration policy. 

Q-learning with $\varepsilon$-greedy exploration does the following update at time $t$:

1. In state $s_t$, take action $a_t$  such that $a_t$ is random with probability $\varepsilon$ and $a_t \in \arg\max_a \hat{Q}_t(s_t,a) $ with probability $1-\varepsilon$;
2. Observe $s_{t+1}$ and reward $r_t$;
3. Compute $\delta_t = r_t + \gamma \max_a \hat{Q}_t(s_{t+1}, a) - \hat{Q}_t(s_t, a_t)$;
4. Update $\hat{Q}_{t+1}(s, a) = \hat{Q}_t(s, a) + \alpha_t(s,a)\delta_t\mathbb{1}\{s=s_t, a=a_t\}  $


##### SARSA

SARSA is similar to Q-learning, but it is an *on-policy* algorithm: it follows a (stochastic) policy $\pi_Q$ and updates its estimate towards the value of this policy. One possible choice is:

$$
\pi_Q(a|s) = \frac{ \exp(\tau^{-1}Q(s,a))  }{\sum_{a'}\exp(\tau^{-1}Q(s,a')) }
$$
where $\tau$ is a "temperature" parameter: when $\tau$ approaches 0, $\pi_Q(a|s)$ approaches the greedy (deterministic) policy $a \in \arg\max_{a'}Q(s,a')$.

At each time $t$, SARSA keeps an estimate $\hat{Q}_t$ of the true Q function and uses $\pi_{\hat{Q}_t}(a|s)$ to choose the action $a_t$. If $\tau \to 0$ with a proper rate as $t \to \infty$, $\hat{Q}_t$ converges to $Q$ and $\pi_{\hat{Q}_t}(a|s)$ converges to the optimal policy $\pi^*$. 

The SARSA update at time $t$ is done as follows:

1. In state $s_t$, take action $a_t \sim \pi_{\hat{Q}_t}(a|s_t)$ ;
2. Observe $s_{t+1}$ and reward $r_t$;
3. Sample the next action $a_{t+1} \sim \pi_{\hat{Q}_t}(a|s_{t+1})$;
4. Compute $\delta_t = r_t + \gamma \hat{Q}_t(s_{t+1}, a_{t+1}) - \hat{Q}_t(s_t, a_t)$
5. Update $\hat{Q}_{t+1}(s, a) = \hat{Q}_t(s, a) + \alpha_t(s,a)\delta_t\mathbb{1}\{s=s_t, a=a_t\}$

this is for discrete action spaces

* 

* 
* 
* 
* 
* 
* 
* 

