Question Link: [https://www.geeksforgeeks.org/problems/brackets-in-matrix-chain-multiplication1024](https://www.geeksforgeeks.org/problems/brackets-in-matrix-chain-multiplication1024)

```cpp
class Solution {
  public:
    void genAns(int st, int end,vector< string >& ans, vector< vector<int> >& divn)
    {
        if(end-st == 0)
            return ;
        genAns(st,divn[st][end],ans,divn) ;
        genAns(divn[st][end]+1,end,ans,divn) ;
        ans[st] = "(" + ans[st] ;
        ans[end] = ans[end] + ")" ;
    }

string matrixChainOrder(vector<int> &arr)
{
    int n = arr.size();
    vector<vector<int>> dp(n-1, vector<int>(n-1)), divn(n-1, vector<int>(n-1,-1)) ;
    for(int size=2 ; size<=n-1 ; size++)
    {
        for(int st=0 ; st+size-1 <= n-2 ; st++)
        {
            dp[st][st+size-1] = INT_MAX ;
            for(int k=st ; k<st+size-1 ; k++)
            {
                if(dp[st][st+size-1] > arr[st]*arr[k+1]*arr[st+size] + dp[st][k] + dp[k+1][st+size-1])
                {
                    dp[st][st+size-1] = arr[st]*arr[k+1]*arr[st+size] + dp[st][k] + dp[k+1][st+size-1] ;
                    divn[st][st+size-1] = k ;
                } 
            }
        }
    }
    
    vector<string> ans(n-1) ;
    for(int i=0 ; i<n-1 ; i++)
        ans[i] = 'A'+i ;
    
    
    genAns(0,n-2,ans,divn);
    
    string fans;
    for(int i=0 ; i<n-1 ; i++)
        fans += ans[i] ;
    
    return fans ;
}
};
```
