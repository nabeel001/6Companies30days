Question Link: [https://www.geeksforgeeks.org/problems/maximum-of-all-subarrays-of-size-k3101](https://www.geeksforgeeks.org/problems/maximum-of-all-subarrays-of-size-k3101)

```cpp
vector<int> maxOfSubarrays(vector<int>& arr, int k) {
        int n = arr.size();
        deque<int> dq;
        vector<int> ans;
        
        for(int i=0;i<n;i++)
        {
            while(!dq.empty() && dq.front() <= i-k)
                dq.pop_front();
            while(!dq.empty() && arr[dq.back()] <= arr[i])
                dq.pop_back();
                
            dq.push_back(i);
            
            if(i>=k-1)
                ans.push_back(arr[dq.front()]);
        }
        
        return ans;
    }
```
