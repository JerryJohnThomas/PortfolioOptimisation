# 8. Dynamic Asset-Allocation and Consumption


## Introduction

1. Periodically decide how one’s investment portfolio should be split across various choices of investment assets
    * The key being how much money to invest in more risky assets (which have potential for high returns on investment) versus less risky assets 
2. Periodically decide how much capital to leave in one’s investment portfolio versus how much money to consume for one’s personal needs/pleasures by extracting money from one’s investment portfolio
    * 

## 8.1. Optimization of Personal Finance
* Components
    * Receiving money
    * Consuming money   
    * Investing Money
    * 
* Goal: To maximize the Expected Aggregated Utility of Consumption of Money over our lifetime 
* States
    * the quantities of money invested in each investment asset,
    * the valuation of the assets invested in,
    * job situation
* Actions
    * investment choice and
    * consuming money for leisure/necessity
* Reward
    * Utility of Consumption of Money
    * second part of action
* Model 
    * uncertainties in situation and stocks

## 8.2. Merton’s Portfolio Problem and Solution
* assumptions
    * have initial wealth of $W_0$
    * we have n risky assets (in this eg we do n=1)
    * we have 1 risk-less asset
    * money consumption is optional (meaning you dont have to pay any loans etc)
    * wealth at any time t (denoted $W_t$) as the aggregate market value of your investment assets.
    *  There are no transaction costs with any of the buy or sell transactions in any of the assets
    * You are allowed to buy or sell any fractional quantities of assets at any point in time (i.e., in continuous time
    * Consumption Utility function is Constant Relative Risk-Aversion (**CRRA**) 
* Math 
    * S: risky asset $d S_t=\mu \cdot S_t \cdot d t+\sigma \cdot S_t \cdot d z_t$
    * R: risk less asset 
    * $d R_t=r \cdot R_t \cdot d t$
    * We denote the fraction of wealth allocated to the risky asset at time t as $π(t, W_t)$
    * fraction of wealth allocated to the riskless asset at time t is 1 - $π(t, W_t)$
    * consumption of wealth $c(t, W_t)$ 
    * 
    * 
* Action: $c_t$ and $\pi_t$ together
* More Maths
    * we try to ma E[U(x)] ny making optimal action (c,$\pi$)
    * B : bequest ,$B_t$ this is the amount of money left for family when you die at time t
    *  
 - The State at time $t$ is $\left(t, W_t\right)$
- The Action at time $t$ is $\left(\pi_t, c_t\right)$
- The Reward per unit time at time $t<T$ is:

* Our goal is to find the Policy : (t, Wt) → (πt, ct) that maximizes the Expected Return`
* Return is cumulative discounted reward
* HJB equation solution

## 8.3. Developing Intuition for the Solution to Merton’s Portfolio Problem
* π∗(t, Wt) is a constant i.e., it is independent of both of the state variables t and Wt
    * no matter our age and our wealth we should always invest
    * The simplicity of the solution means that asset allocation is straightforward—we just need to keep re-balancing to maintain this balance


## GETS COMPLEX FROM HERE
* stopped temporarly
