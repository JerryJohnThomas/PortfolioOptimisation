# Problem 4 : Optimal Trade Order Execution

## Trading Order Book
The order book shows how many limit orders are active at each price level at the current moment. It is used to review the current market depth and estimate the the filled price of a market order.

<img src = 'assets/OB.png' style='width:50%;'></img>

p_0(b) is best bid, p_0(a) is best ask.

best bid = largest price bid

best ask = smallest price ask

mid  = avg(best bid + best ask)

spread = best ask - best bid

market depth = largest ask value - smallest bid value

Buy LO(P,N) , willingness to buy N shares at price <= P

Sell LO(P,N), willingness to sell N shares at price >= P

## Price Impact
Changes caused when market order alters Order book. 

## Optimal Trade Order Execution Problem
- Sell large number N of shares
- Allowed to trade in T discrete time steps
- Only Allowed to submit market orders 
- Considering both permanent and temporary price impact
- Goal is to maximize Expected Total Utility of Sales Proceeds

Total Utility of Sales Proceeds ?
aggregate amount of satisfaction received from selling of the stocks.

- Break N in appropriate chunks
    - sell too fast, bad prices
    - sell too slow, running out of time
    - selling slowly leads to uncertain proceeds
- Dynamic Optimization problem
> We can model this as Markov Decision Process

