Question Link: [https://leetcode.com/problems/first-unique-character-in-a-string](https://leetcode.com/problems/first-unique-character-in-a-string)

```cpp
class Solution {
public:
    int firstUniqChar(string s) {
        int ans = -1;
        int n = s.length();
        map<char,int>mp;
        
        for(int i=0;i<n;i++)
                mp[s[i]]++;
        
        for(int i=0;i<n;i++)
        {
            if(mp[s[i]]==1)
                return i;
        }
        
        return ans;
    }
};
```
