## 669. Trim a Binary Search Tree - 修剪二叉搜索树

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉搜索树，同时给定最小边界<code>L</code>&nbsp;和最大边界&nbsp;<code>R</code>。通过修剪二叉搜索树，使得所有节点的值在<code>[L, R]</code>中 (R&gt;=L) 。你可能需要改变树的根节点，所以结果应当返回修剪好的二叉搜索树的新的根节点。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> 
    1
   / \
  0   2

  L = 1
  R = 2

<strong>输出:</strong> 
    1
      \
       2
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> 
    3
   / \
  0   4
   \
    2
   /
  1

  L = 1
  R = 3

<strong>输出:</strong> 
      3
     / 
   2   
  /
 1
</pre>



-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/trim-a-binary-search-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/trim-a-binary-search-tree/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 20  ms | 2.1 MB |

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
    TreeNode* trimBST(TreeNode* root, int L, int R) {
        if (!root) { return root; }
        if (root->val < L) {
            return trimBST(root->right, L, R);
        }
        if (root->val > R) {
            return trimBST(root->left, L, R);
        }
        
        root->left = trimBST(root->left, L, R);
        root->right = trimBST(root->right, L, R);
        return root;
    }
};
```
