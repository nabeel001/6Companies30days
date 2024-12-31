Question Link: [https://leetcode.com/problems/image-smoother/](https://leetcode.com/problems/image-smoother/)

```cpp
class Solution {
public:
    vector<vector<int>> imageSmoother(vector<vector<int>>& img) {
        int m = img.size();
        int n = img[0].size();
        vector<vector<int>> ans(m, vector<int>(n, 0));

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                int sum = 0;
                int ct = 0;

                // 3x3 filter
                for (int r = -1; r <= 1; r++) {
                    for (int c = -1; c <= 1; c++) {
                        int ni = i + r;
                        int nj = j + c;
                        if (ni >= 0 && ni < m && nj >= 0 && nj < n) {
                            sum += img[ni][nj];
                            ct++;
                        }
                    }
                }
                ans[i][j] = sum / ct;
            }
        }
        return ans;
    }
};
```
