## 938. Range Sum of BST - 二叉搜索树的范围和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定二叉搜索树的根结点&nbsp;<code>root</code>，返回 <code>L</code> 和 <code>R</code>（含）之间的所有结点的值的和。</p>

<p>二叉搜索树保证具有唯一的值。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>root = [10,5,15,3,7,null,18], L = 7, R = 15
<strong>输出：</strong>32
</pre>

<p><strong>示例&nbsp;2：</strong></p>

<pre><strong>输入：</strong>root = [10,5,15,3,7,13,18,1,null,6], L = 6, R = 10
<strong>输出：</strong>23
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>树中的结点数量最多为&nbsp;<code>10000</code>&nbsp;个。</li>
	<li>最终的答案保证小于&nbsp;<code>2^31</code>。</li>
</ol>



-----

题目标签：Tree / Recursion

题目链接：[LeetCode](https://leetcode.com/problems/range-sum-of-bst/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/range-sum-of-bst/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 152  ms | 41.2 MB |

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
    void dfs(TreeNode* root, int L, int R, int& ret) {
        if (!root) return;
        if (root->val >= L && root->val <= R)
            ret += root->val;
        dfs(root->left, L, R, ret);
        dfs(root->right, L, R, ret);
    }

    int rangeSumBST(TreeNode* root, int L, int R) {
        int res = 0;
        dfs(root, L, R, res);
        return res;
    }
};
```
