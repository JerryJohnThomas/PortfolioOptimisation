# actions

[action_stock1 , action_stock2, .... action_stockn]

Actions: They are the outputs of the network for a given period, and they represent the final portfolio
weights, i.e., the percentage of each asset within the portfolio.

action_stock1 < 0 : means sell that much percentage
action_stock1 > 0 : means buy that much percentage
action_stock1 = 0 : means hold


## Observation space

State: It is the input used to feed the network and describes the current situation of the stock market
via financial indicators. These indicators are made of a tensor of features, which includes 
* the current balance of our portfolio
* the stock prices
* the owned assets


self.state = [INITIAL_ACCOUNT_BALANCE] + self.data.values.tolist() + [0]*self.stock_dim

self.state[0] = INITIAL_ACCOUNT_BALANCE


DBT:


they assume in buy and sell that actions will be 5.67 means you buy 5 stocks and stuff, but we defined it to be [-1 or 1] ???
possible answers 
* `actions = actions * HMAX_NORMALIZE`


sell_index = argsort_actions[:np.where(actions < 0)[0].shape[0]]
argsort is in the increasing order, 
actions < 0 gives us the count of the actions < 0
so we just take the first n indcies which are for selling

argsort_actions[::-1] :: this reverses the list
and do the above thing to get buying stuff > 0 
 
arr * 10 : makes concatenate 10 times 
np_arr * 10 : makes each value 10 times and not concatenate (this is being done here)




