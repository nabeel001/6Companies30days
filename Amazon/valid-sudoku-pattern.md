Question Link: [https://leetcode.com/problems/valid-sudoku](https://leetcode.com/problems/valid-sudoku)

```cpp
class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
       
        for(int i=0;i<9;i++)
        {
            map<char,bool>mp;
            for(int j=0;j<9;j++)
            {
                if(mp[board[i][j]] and board[i][j]!='.')
                    return false;
                else
                    mp[board[i][j]] = true;
            }
        }
        
        for(int i=0;i<9;i++)
        {
            map<char,bool>mp;
            for(int j=0;j<9;j++)
            {
                if(mp[board[j][i]] and board[j][i]!='.')
                    return false;
                else
                    mp[board[j][i]] = true;
            }
        }
        
        for(int i=0;i<9;i+=3)
        {
            map<char,bool>mp1;
            for(int r=i;r<i+3;r++)
            {
                for(int c=0;c<3;c++)
                {
                    if(mp1[board[r][c]] and board[r][c]!='.')
                        return false;
                    else
                        mp1[board[r][c]] = true;
                }
            }
            
            map<char,bool>mp2;
            for(int r=i;r<i+3;r++)
            {
                for(int c=3;c<6;c++)
                {
                    if(mp2[board[r][c]] and board[r][c]!='.')
                        return false;
                    else
                        mp2[board[r][c]] = true;
                }
            }
            
            map<char,bool>mp3;
            for(int r=i;r<i+3;r++)
            {
                for(int c=6;c<9;c++)
                {
                    if(mp3[board[r][c]] and board[r][c]!='.')
                        return false;
                    else
                        mp3[board[r][c]] = true;
                }
            }
        }
        
        return true;
    }
};
```
