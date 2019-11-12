## 144. Binary Tree Preorder Traversal - 二叉树的前序遍历

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，返回它的&nbsp;<em>前序&nbsp;</em>遍历。</p>

<p>&nbsp;<strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,null,2,3]  
   1
    \
     2
    /
   3 

<strong>输出:</strong> [1,2,3]
</pre>

<p><strong>进阶:</strong>&nbsp;递归算法很简单，你可以通过迭代算法完成吗？</p>



-----

题目标签：Stack / Tree

题目链接：[LeetCode](https://leetcode.com/problems/binary-tree-preorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-preorder-traversal/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 884.7 KB |

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
    vector<int> res;
    void preorder(TreeNode* node) {
        if (!node) return;
        res.push_back(node->val);
        preorder(node->left);
        preorder(node->right);
    }

    vector<int> preorderTraversal(TreeNode* root) {
        preorder(root);
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
