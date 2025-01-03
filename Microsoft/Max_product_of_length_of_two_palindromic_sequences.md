Question Link: [https://leetcode.com/problems/maximum-product-of-the-length-of-two-palindromic-subsequences](https://leetcode.com/problems/maximum-product-of-the-length-of-two-palindromic-subsequences)

```
Simple explanation :
3 possibilities :-

    1) pick s[i] for s1 but don't pick s[i] for s2 (because they should be disjoint)
       - explore this path and find the result (and then backtrack)

    2) pick s[i] for s2 but don't pick s[i] for s1 (because they should be disjoint)
        - explore this path and find the result (and then backtrack)

    3) don't pick s[i] at all - explore this path and find the result
        (and then backtrack)

In any of the path, if I get s1 and s2 both as palindrome, update our
result with maximum length. It's like a classic Backtrack approach.
```

```cpp
class Solution {

public:
    int result = 0;
    bool isPalin(string& s) {
        int i = 0, j = s.length() - 1;
        while (i < j) {
            if (s[i++] != s[j--])
                return false;
        }
        return true;
    }

    void dfs(string& s, int id, string& s1, string& s2) {
        if (id >= s.length()) {
            if (isPalin(s1) && isPalin(s2))
                result = max(result, (int)s1.length() * (int)s2.length());
            return;
        }

        s1.push_back(s[id]);
        dfs(s, id + 1, s1, s2);
        s1.pop_back();

        s2.push_back(s[id]);
        dfs(s, id + 1, s1, s2);
        s2.pop_back();

        dfs(s, id + 1, s1, s2);
    }

    int maxProduct(string s) {
        string s1 = "", s2 = "";
        dfs(s, 0, s1, s2);
        return result;
    }
};
```
