# Chapter 9 :  Derivatives Pricing and Hedging

## Links youtube
* very basic idea of derivates in 1 min - [link](https://www.youtube.com/watch?v=gCHiLLgO55o)
* good idea of derivatives - [link](https://www.youtube.com/watch?v=LQrBzl0DMBA)


* the word hedging refers to reducing or eliminating market risks associated with a derivative
* The **application 1** is to identify the optimal time/state to exercise an American Option
    * An American option is a style of options contract that allows holders to exercise their rights at any time before and including the expiration date
*  The **application2** is to identify the optimal hedging strategy for derivatives in real-world situations

## 9.1. A Brief Introduction to Derivatives

* a derivative is a legal contract between the derivative buyer and seller that either:
    * 
    * 
    * 




### 9.1.1. Forwards
* buyer says will buy for price K 
* seller says will sell at price K
* both after some days at t=T
* stock price at time t is $S_t$
* now at the day there is no option but to sell and buy, 
* buyer can immediately sell off and get a profit called payoff as $S_T$ - K
* sim for seller K - $S_T$ 
* 


### European
* The option to exercise is available only at a fixed point in time t = T

#### Call option
* the buyer can buy or can say I dont want to buy
* so buyer will be never at loss
* so buyer needs to pay some additional price for this added benefit called Option Pricing

#### Put option
* owner has right to sell or not to sell 

### 9.1.3. American Options
* We can exercise the option to buy (in the case of Call) or sell (in the case of Put) at any time t ≤ T. 
* The problem of pricing an American Option is much harder

Use of derivatives 
*  The first reason is to protect against adverse market movements that might damage the value of one’s portfolio - this is known as hedging
* 

Stuff
* American Option Pricing is Optimal Stopping, and hence an MDP





for problem 2
* medium.com/swlh/option-pricing-using-reinforcement-learning-ad2ddca7735b
* optimal stopping problem

For problem 3
* only DRL works and the paper is Deephedging
* only ref by finrl and sir
* https://github.com/hansbuehler/deephedging
* https://arxiv.org/abs/1802.03042



Did not go into much detail here


problem 4
* The first problem is Optimal Execution of the sale of a large number of shares of a stock so as to yield the maximum utility of sales proceeds over a finite horizon

problem 5
* The second problem is Optimal Market-Making, i.e., the optimal bids
(willingness to buy a certain number of shares at a certain price) and asks (willingness to sell a certain number of shares at a certain price) to be 
submitted on the Order Book

