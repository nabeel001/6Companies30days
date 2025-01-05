Question Link: [https://leetcode.com/problems/rotting-oranges](https://leetcode.com/problems/rotting-oranges)

```cpp
class Solution {
public:
    int orangesRotting(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
        queue<pair<int,int>>qu;
        
        int tot_count, qu_count;
        tot_count = qu_count = 0;
        
        for(int i=0;i<m;i++)
        {
            for(int j=0;j<n;j++)
            {
                if(grid[i][j] == 2)
                    qu.push(make_pair(i,j));

                if(grid[i][j] != 0)
                    tot_count++;
            }
        }
        
        int dx[4] = {0,0,1,-1};
        int dy[4] = {1,-1,0,0};
        int mins = 0;
        
        while(!qu.empty())
        {
            int qu_sz = qu.size();
            qu_count += qu_sz;
            
            while(qu_sz--)
            {
                auto id = qu.front();
                qu.pop();
                int row = id.first;
                int col = id.second;
                
                for(int i=0;i<4;i++)
                {
                    int nxt_row = row + dx[i];
                    int nxt_col = col + dy[i];
                    
                    if(nxt_row<0 || nxt_row>=m || nxt_col<0 || nxt_col>=n || grid[nxt_row][nxt_col]!=1)
                        continue;
                    
                    grid[nxt_row][nxt_col] = 2;
                    qu.push(make_pair(nxt_row,nxt_col));
                }
            }
            if(!qu.empty())
                mins++;            
        }
        
        return ((tot_count == qu_count) ? mins : -1);
    }
};
```
