Question Link: [https://leetcode.com/problems/count-the-number-of-incremovable-subarrays-i](https://leetcode.com/problems/count-the-number-of-incremovable-subarrays-i)

```cpp
class Solution {
public:
    bool isIncreasing(int i, int j, vector<int>& nums) {
        int prev = INT_MIN;
        for (int id = 0; id < nums.size(); id++) {
            if (id < i || id > j) {
                if (nums[id] > prev) {
                    prev = nums[id];
                } else
                    return false;
            }
        }
        return true;
    }
    int incremovableSubarrayCount(vector<int>& nums) {
        int n = nums.size();
        int ans = 0;
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                ans += isIncreasing(i, j, nums) ? 1 : 0;
            }
        }
        return ans;
    }
};
```
