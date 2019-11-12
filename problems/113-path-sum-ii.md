## 113. Path Sum II - 路径总和 II

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树和一个目标和，找到所有从根节点到叶子节点路径总和等于给定目标和的路径。</p>

<p><strong>说明:</strong>&nbsp;叶子节点是指没有子节点的节点。</p>

<p><strong>示例:</strong><br>
给定如下二叉树，以及目标和&nbsp;<code>sum = 22</code>，</p>

<pre>              <strong>5</strong>
             / \
            <strong>4</strong>   <strong>8</strong>
           /   / \
          <strong>11</strong>  13  <strong>4</strong>
         /  \    / \
        7    <strong>2</strong>  <strong>5</strong>   1
</pre>

<p>返回:</p>

<pre>[
   [5,4,11,2],
   [5,8,4,5]
]
</pre>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/path-sum-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/path-sum-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 1.4 MB |

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
static auto _ = [](){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    vector<vector<int>> res;
    void dfs(TreeNode* node, int sum, vector<int>& path) {
        if (!node) {
            return;
        }
        if (sum == 0 && !node->left && !node->right) {
            res.push_back(path);
            return;
        }
        if (node->left) {
            path.push_back(node->left->val);
            dfs(node->left, sum - node->left->val, path);
            path.pop_back();
        }
        if (node->right) {
            path.push_back(node->right->val);
            dfs(node->right, sum - node->right->val, path);
            path.pop_back();
        }
    }

    vector<vector<int>> pathSum(TreeNode* root, int sum) {
        if (!root) return res;
        vector<int> path;
        path.push_back(root->val);
        dfs(root, sum - root->val, path);
        return res;
    }
};
```
