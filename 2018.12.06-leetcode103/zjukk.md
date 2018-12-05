```
class Solution {
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        if (!root) return {};
        vector<vector<int>> res;
        queue<TreeNode*> q;
        q.push(root);
        TreeNode* node;
        bool fromLeft = true;
        while (!q.empty()) {
            vector<int> tmp;
            int size = q.size();
            for (int i = 0; i < size; ++i) {
                node = q.front();
                q.pop();
                if (fromLeft)
                tmp.push_back(node->val);
                else 
                tmp.insert(tmp.begin(),node->val);
                if (node->left) q.push(node->left);
                if (node->right) q.push(node->right);
            }
            res.push_back(tmp);
            fromLeft = !fromLeft;
        }
        return res;
    }
};
```
