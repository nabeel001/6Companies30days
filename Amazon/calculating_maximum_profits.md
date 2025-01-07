Question Link: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv)

```cpp
class Solution {
public:
    // id -> index of the day
    // is_buy -> whether allowed to buy the stock or not
    // tx -> no.transactions left
    int sol(int id, int is_buy, int tx, vector<int> &prices, vector<vector<vector<int>>>&dp)
    {
        if(tx == 0)
            return 0; //no more buying or selling as tx limit over
        if(id == prices.size())
            return 0; //no more buying or selling as days exhausted
        
        if(dp[id][is_buy][tx] != -1)
            return dp[id][is_buy][tx]; 
        
        int profit_1 = 0;
        int profit_2 = 0;
        
        if(is_buy) //buy
        {
            profit_1 = sol(id+1, 0, tx, prices, dp) - prices[id]; // buy
            profit_2 = sol(id+1, 1, tx, prices, dp); // not buy
        }
        else //sell
        {
            profit_1 = sol(id+1, 1, tx-1, prices, dp) + prices[id]; // sell & tx complete
            profit_2 = sol(id+1, 0, tx, prices, dp); // not sell
        }
        return dp[id][is_buy][tx] = max(profit_1 , profit_2);
    }
    
    int maxProfit(int k, vector<int>& prices) {
        
        int n = prices.size();
        
        // (id,is_buy,tx)
        vector<vector<vector<int>>> dp(n,vector<vector<int>>(2,vector<int>(k+1,-1))); 
        return sol(0, 1, k, prices, dp);
    }
};
```
