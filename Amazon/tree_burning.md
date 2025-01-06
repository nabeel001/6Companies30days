Question Link: [https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected](https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected)

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left),
 * right(right) {}
 * };
 */
class Solution {
public:
    unordered_map<int, vector<int>> graph;

    int amountOfTime(TreeNode* root, int start) {
        constructGraph(root);
        vector<bool> vis(100001);
        queue<int> q;
        q.push(start);
        vis[start] = true;
        int time = -1;

        while (!q.empty()) {
            time++;
            int len = q.size();
            for (int i = 0; i < len; i++) {
                int node = q.front();
                q.pop();
                for (auto it : graph[node]) {
                    if (!vis[it]) {
                        q.push(it);
                        vis[it] = true;
                    }
                }
            }
        }
        return time;
    }

    void constructGraph(TreeNode* root) {
        if (!root)
            return;

        if (root->left) {
            graph[root->val].push_back(root->left->val);
            graph[root->left->val].push_back(root->val);
        }

        if (root->right) {
            graph[root->val].push_back(root->right->val);
            graph[root->right->val].push_back(root->val);
        }

        constructGraph(root->left);
        constructGraph(root->right);
    }
};
```
