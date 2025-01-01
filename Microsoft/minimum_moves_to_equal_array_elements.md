Question Link: [https://leetcode.com/problems/minimum-moves-to-equal-array-elements-ii](https://leetcode.com/problems/minimum-moves-to-equal-array-elements-ii)

```cpp
class Solution {
public:
    int minMoves2(vector<int>& nums) {
        int n = nums.size(), ans = 0;
        sort(nums.begin(), nums.end());
        for(int i=0; i<n; i++){
            ans += abs(nums[i] - nums[n/2]); //median of the array is the common value
        }
        return ans;
    }
};
```
