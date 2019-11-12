## 145. Binary Tree Postorder Traversal - 二叉树的后序遍历

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，返回它的 <em>后序&nbsp;</em>遍历。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,null,2,3]  
   1
    \
     2
    /
   3 

<strong>输出:</strong> [3,2,1]</pre>

<p><strong>进阶:</strong>&nbsp;递归算法很简单，你可以通过迭代算法完成吗？</p>



-----

题目标签：Stack / Tree

题目链接：[LeetCode](https://leetcode.com/problems/binary-tree-postorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-postorder-traversal/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 9.2 MB |

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
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> res;
        stack<pair<bool, TreeNode*>> stk;
        stk.push({false, root});
        while (!stk.empty()) {
            auto p = stk.top();
            stk.pop();
            bool flag = p.first;
            TreeNode* node = p.second;
            if (!node) continue;
            if (flag) {
                res.push_back(node->val);
            } else {
                stk.push({true, node});
                stk.push({false, node->right});
                stk.push({false, node->left});
            }
        }
        return res;
    }
};
```
