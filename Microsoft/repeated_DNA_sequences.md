Question Link: [https://leetcode.com/problems/repeated-dna-sequences](https://leetcode.com/problems/repeated-dna-sequences)

```cpp
class Solution {
public:
    vector<string> findRepeatedDnaSequences(string s) {
        int n = s.length();
        unordered_map<string,int> mp;

        if(n <= 10)
            return {};
           
        int i=0;
        vector<string> ans;
        while(i+9 < n){
            string ss = s.substr(i++, 10);
            mp[ss]++;
        }

        for(auto it:mp){
            if(it.second > 1)
                ans.push_back(it.first);
        }

        return ans;
    }
};
```
