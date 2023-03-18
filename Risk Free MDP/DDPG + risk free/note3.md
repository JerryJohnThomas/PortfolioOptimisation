# NOTE 3 

sorted writing of findings


4 things

1. borker paper equations
2. coded equations
3. DDPG equations
4. our new equations


## Borker equations


<!-- ###  -->
Q/Critic Loss

$$
Q_{n+1}(i, u)=Q_n(i, u)+a(v(i, u, n)) I\left\{X_n=i, Z_n=u\right\}\left(\frac{\mathrm{e}^{c\left(X_n, Z_n\right)} Q_n\left(X_{n+1}, Z_{n+1}\right)}{Q_n\left(i_0, u_0\right)}-Q_n(i, u)\right)
$$


$$
Q_{Loss} = \left(\frac{\mathrm{e}^{c\left(X_n, Z_n\right)} Q_n\left(X_{n+1}, Z_{n+1}\right)}{Q_n\left(i_0, u_0\right)}-Q_n(i, u)\right)
$$


$$\forall \textbf{ state}$$


<!-- ### -->
 Policy/Actor Loss

$$
\pi^{n+1}(i, u)=\Gamma\left(\pi^n(i, u)+b(v(i, u, n)) I\left\{X_n=i, Z_n=u\right\}\left(Q_n(i, u)-Q_n\left(i, u_0\right)\right)\right.
$$

$$\forall \textbf{ state, action}$$

Observations
* Q_loss is dependent on Q only
* Policy Loss is dep on Policy and Q
* risk sensitivity factor in Q only 


## Coded equations 

Actor Loss
* $Q_{loss} = (Q_{target}-Q(s,a))^2$
* $Q_{target} = \frac{Q(s_{t+1},a_{t+1})}{Q(s_{ref},a_{ref})}*e^{-reward} - \alpha * action\_log\_prob - Q(s_t,a_t)$


Critic Loss
* SAC like 


## DDPG 


Critic Loss
* original discrete state space 
* ![](https://spinningup.openai.com/en/latest/_images/math/31dda6ac0678255c4e192dd6fae4f7ed3c7cd91b.svg)
* convert to cts space by using actor network
* ![](https://spinningup.openai.com/en/latest/_images/math/4421120861d55302d76c7e2fd7cc5b2da7aea320.svg)

Actor Loss
*  ![](https://spinningup.openai.com/en/latest/_images/math/cc4e3565d839e63e871a1cf7e3ce5e95bb616b29.svg)
* we just need to maximise the Q values so actor_loss = - Q

## final formulations

observations :
* **Borker:** Q-loss has risk sensitivity part 
* **Borker:** Q-loss and $\pi$ has discrete problem 
* **DDPG**: convert Q from discrete to cts space
* DBT: What to do with the $\pi$ loss, 
    * should we follow the DDPG model  
    * or something else

new formulations

Q/Critic Loss 

$$
Q_{Loss} = \left(\frac{\mathrm{e}^{c\left(X_n, Z_n\right)} Q_n\left(X_{n+1}, \pi(u)\right)}{Q_n\left(i_0, u_0\right)}-Q_n(i, u)\right)
$$

