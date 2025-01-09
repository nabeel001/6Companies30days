Question Link: [https://leetcode.com/problems/serialize-and-deserialize-binary-tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree)

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Codec {
public:

    // Encodes a tree to a single string.
    string serialize(TreeNode* root) {
        
        string str = "";
        
        if(root == NULL)
            return str;
        
        queue<TreeNode*>qu;
        qu.push(root);
        
        while(!qu.empty())
        {
            TreeNode *node = qu.front();
            qu.pop();
            
            if(node == NULL)
                str += "#,";
            else
            {
                str += to_string(node->val) + ',';
                qu.push(node->left);
                qu.push(node->right);
            }
        }
    
        return str;
    }

    // Decodes your encoded data to tree.
    TreeNode* deserialize(string data) {
        
        if(data == "")
            return NULL;
         
        string value;
        stringstream ss(data);
        
        getline(ss , value , ',');
        TreeNode *root = new TreeNode(stoi(value));
        
        queue<TreeNode*>qu;
        qu.push(root);
        
        while(!qu.empty())
        {
            TreeNode* node = qu.front();
            qu.pop();
            
            getline(ss , value , ',');
            if(value != "#")
            {
                node->left = new TreeNode(stoi(value));
                qu.push(node->left);
            }
            
            getline(ss , value , ',');
            if(value != "#")
            {
                node->right = new TreeNode(stoi(value));
                qu.push(node->right);
            }
        }
        
        return root;
    }
};
```
