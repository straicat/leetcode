## 94. Binary Tree Inorder Traversal - 二叉树的中序遍历

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，返回它的<em>中序&nbsp;</em>遍历。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,null,2,3]
   1
    \
     2
    /
   3

<strong>输出:</strong> [1,3,2]</pre>

<p><strong>进阶:</strong>&nbsp;递归算法很简单，你可以通过迭代算法完成吗？</p>



-----

题目标签：Stack / Tree / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/binary-tree-inorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 9.1 MB |

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
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        stack<pair<int, TreeNode*>> stk;
        stk.push({0, root});
        while (!stk.empty()) {
            auto p = stk.top();
            stk.pop();
            int flag = p.first;
            TreeNode* node = p.second;
            if (!node) continue;
            if (flag == 0) {
                stk.push({0, node->right});
                stk.push({1, node});
                stk.push({0, node->left});
            } else {
                res.push_back(node->val);
            }
        }
        return res;
    }
};
```
