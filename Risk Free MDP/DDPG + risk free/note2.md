# Note - 2 : Replacement Mathematical foundations

## key understandings from Note
* basically instead of maxxing it, we replace it with policy net target
* we can investigate more into why it works mathematically. or 
* think how we can include them in boaker paper
* lets do the former now


## Attempt 0 (chatgpt)
* 
* 
* 
* 

## Attempt 1 (From paper DDPG)
* in one note 
* not much proof is there. it converts from DPG to DDPG so not sure if this is the paper to go to.
* So lets learn about DPG 

## DPG Attempt 0
* [ref](https://medium.com/geekculture/introduction-to-deterministic-policy-gradient-dpg-e7229d5248e2)
* our goal is to maximize a performance measure function $J(θ) = E[r_γ |π]$, which is the expected total discounted reward following policy π, where θ is the parameters of the function we are updating
* **Here is an expanded version of the performance measure function where we sum up all rewards over the state distribution ρ and actions in each state.**
* ![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*SFxJ1_-Jib1mmP4tpqWXxQ.png)
* Unlike a stochastic policy, we define our policy to be the function μ_θ: S → A
* we only need to sum over the state space as action is deterministic
* ![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*lDUqRlMwoIANICSWliYrhw.png)
* For the deterministic policy, we will be doing something similar. Since our action space is continuous, we will move our policy in the direction of the Q function’s gradient. Instead of maximizing Q by taking the argmax action, the policy will converge towards a maxima Q value.
* ![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*rybaibq_77yrGFJBsy6uNQ.png)
* ![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*nNxihIu80_yHzvYeR8ynBA.png)
* ![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*1Lej3d1W4udXhrHc7roeGg.png)
* This seems to be a good road to go down to ... lets explore more
* 
* 




