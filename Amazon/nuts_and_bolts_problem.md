Question Link: [https://www.geeksforgeeks.org/problems/nuts-and-bolts-problem0431](https://www.geeksforgeeks.org/problems/nuts-and-bolts-problem0431)

```cpp
void matchPairs(int n, char nuts[], char bolts[]) 
    {
                      //  0    1    2    3    4    5    6    7    8  
        char order[] = { '!', '#', '$', '%', '&', '*', '?', '@', '^'};
        int pos = 0;
        for(int i = 0; i < 9; i++)
        {
            for(int j = 0; j < n; j++)
            {
                if(order[i] == bolts[j])
                {
                    swap(bolts[j], bolts[pos]);
                    nuts[pos] = bolts[pos++];
                }
            }
        }
    }
```
