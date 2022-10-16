# Model-Free Reinforcement Learning for Asset Allocation


Remarks
* Authors - Carnegie Mellon University (qs 52), JP Morgan, Africa
* https://www.linkedin.com/in/srijansood/
* 
* 

## 1. Introduction

### 1.1 Background

Asset allocation (or portfolio management) is the task of determining how to optimally allocate funds of a finite budget into a range of financial instruments/assets
such as stocks (Filos, 2019). Coming up with a profitable trading strategy involves
making critical decisions on allocating capital into different stock options. Usually,
this allocation should maximize the expected return while minimizing the investment
risks involved (Gao et al., 2021)


While many of these state-of-the-art models achieve good results, there are some
limitations
1. First, they are **overly reliant on using predictive models** (Adämmer &
Schüssler, 2020). These predictive models are not usually too successful at predicting
the financial markets since these markets are highly stochastic and thus are very
difficult to predict accurately
1. many of these models make simplistic and usually **unrealistic assumptions
around the financial signals’** second-order and higher-order statistical moments (Gao
et al., 2021).
1. Finally, these models are usually limited to **discrete action spaces** to
make the resulting models tractable to solve

### 1.3 Aim and Objectives

This study investigates the effectiveness of model-free deep reinforcement learning
agents with portfolio management. The specific objectives are:
* Training RL agents on real-world prices of a finite set of stocks to optimally
allocate a finite cash budget into a range of securities in a portfolio.
* Comparing the performance of RL agents to baseline agents.
* Comparing the performance of value-based RL agents to policy-based RL
agents.
* Comparing the performance of off-policy RL agents to on-policy RL agents.


### 1.4 Research Questions
At the end of this report, we should be able to answer the following questions:
1. How well can RL agents perform the task of portfolio management?
2. Are RL agents markedly better than the classical state-of-the-art portfolio
management techniques?
3. Are there certain classes of RL agents that are consistently better at portfolio
management?



### others
* Since Harry Markowitz proposed the idea of portfolio formation in 1952 to improve
expected rewards and reduce the investment risk, portfolio trading has been the
dominant strategy for many traders
* This study aims to
understand if RL can uncover strategies for portfolio management that yield better
results than the current state of the art methods.


## 2. Portfolio Management


* Portfolio management involves selecting and managing a collection of assets in order
to meet long-term financial goals while adhering to a risk tolerance level. 
* Diversification and portfolio optimization are critical components of efficient portfolio managemen
* What is a Portfolio ?
    * A portfolio is a collection of several financial assets.
* What is Portfolio optmisation ?
    * Portfolio optimization is the process of determining the optimum portfolio from a set of all possible portfolios with a specific goal in mind.



### 2.2 Markowitz Model
* The Markowitz model (Markowitz, 1952) is regarded as one of the first efforts to
codify and propose an optimization strategy for portfolio management mathematically. 









