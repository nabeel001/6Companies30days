Question Link: [https://leetcode.com/problems/count-number-of-nice-subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays)

Best explanation: [https://leetcode.com/problems/count-number-of-nice-subarrays/solutions/508217/c-visual-explanation-o-1-space-two-pointers](https://leetcode.com/problems/count-number-of-nice-subarrays/solutions/508217/c-visual-explanation-o-1-space-two-pointers)

```cpp
class Solution {
public:
    int numberOfSubarrays(vector<int>& nums, int k) {
        int n = nums.size();
        int j = 0, odd = 0, count = 0, total = 0;

        for (int i = 0; i < n; i++) {
            if (nums[i] & 1) // odd
            {
                odd++;
                if (odd >= k) {
                    count = 1;
                    while (!(nums[j] & 1)) // left pointer j is even
                    {
                        j++;
                        count++;
                    }
                    total += count;
                }
            } else if (odd >= k)
                total += count;
        }
        return total;
    }
};
```
