Question Link: [https://leetcode.com/problems/wiggle-sort-ii](https://leetcode.com/problems/wiggle-sort-ii)

### Logic: 
Sort and then write the smaller half of the numbers on the even indexes and the larger half of the numbers on the odd indexes, both from the back. Example:
```
Small half:    4 . 3 . 2 . 1 . 0 .
Large half:    . 9 . 8 . 7 . 6 . 5
----------------------------------
Together:      4 9 3 8 2 7 1 6 0 5
```

```cpp
class Solution {
public:
    void wiggleSort(vector<int>& nums) {
        int n = nums.size();
        vector<int> sorted(nums);
        sort(sorted.begin(), sorted.end());
        int first_half_id = 0;
        int second_half_id = (n + 1) / 2;
        for (int i = nums.size() - 1; i >= 0; i--) {
            nums[i] = sorted[i & 1 ? second_half_id++ : first_half_id++];
        }
    }
};
```
