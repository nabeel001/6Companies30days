Question Link: [https://leetcode.com/problems/longest-mountain-in-array](https://leetcode.com/problems/longest-mountain-in-array)

O(N) time and O(N) space:
```cpp
class Solution {
public:
    int longestMountain(vector<int>& arr) {
        int n = arr.size();
        stack<int> st;
        int ans = 0;

        for(int i=0;i<n;i++){
            if(st.empty() || arr[i] > st.top()){
                st.push(arr[i]);
            }
            else if(arr[i] == st.top()){
                st = stack<int>();
                st.push(arr[i]);
            }
            else{
                int prev = st.top();
                int ct = 0;
                while(i<n && arr[i] < prev){
                    prev = arr[i];
                    i++;
                    ct++;
                }
                if(st.size() >= 2)
                    ans = max(ans, (int)st.size() + ct);
                st = stack<int>();
                st.push(arr[--i]);
            }
        }
        return ans;
    }
};
```

O(N) time and O(1) space:

```cpp
    int longestMountain(vector<int> A) {
        int N = A.size(), res = 0;
        vector<int> up(N, 0), down(N, 0);
        for (int i = N - 2; i >= 0; --i)
            if (A[i] > A[i + 1]) down[i] = down[i + 1] + 1;
        for (int i = 0; i < N; ++i) {
            if (i > 0 && A[i] > A[i - 1]) up[i] = up[i - 1] + 1;
            if (up[i] && down[i]) res = max(res, up[i] + down[i] + 1);
        }
        return res;
    }
```

