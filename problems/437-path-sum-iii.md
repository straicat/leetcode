## 437. Path Sum III - 路径总和 III

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，它的每个结点都存放着一个整数值。</p>

<p>找出路径和等于给定数值的路径总数。</p>

<p>路径不需要从根节点开始，也不需要在叶子节点结束，但是路径方向必须是向下的（只能从父节点到子节点）。</p>

<p>二叉树不超过1000个节点，且节点数值范围是 [-1000000,1000000] 的整数。</p>

<p><strong>示例：</strong></p>

<pre>root = [10,5,-3,3,2,null,11,3,-2,null,1], sum = 8

      10
     /  \
    <strong>5</strong>   <strong>-3</strong>
   <strong>/</strong> <strong>\</strong>    <strong>\</strong>
  <strong>3</strong>   <strong>2</strong>   <strong>11</strong>
 / \   <strong>\</strong>
3  -2   <strong>1</strong>

返回 3。和等于 8 的路径有:

1.  5 -&gt; 3
2.  5 -&gt; 2 -&gt; 1
3.  -3 -&gt; 11
</pre>



-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/path-sum-iii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/path-sum-iii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 20  ms | 1.6 MB |

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
    int pSum(TreeNode* node, int sum) {
        if (!node) { return 0; }
        int r = node->val == sum;
        if (!node->left && !node->right) {
            return r;
        }
        r += pSum(node->left, sum - node->val);
        r += pSum(node->right, sum - node->val);
        return r;
    }

    void dfs(TreeNode* node, int sum, int& rst) {
        if (!node) {
            return;
        }
        rst += pSum(node, sum);
        dfs(node->left, sum, rst);
        dfs(node->right, sum, rst);
    }

    int pathSum(TreeNode* root, int sum) {
        int res = 0;
        dfs(root, sum, res);
        return res;
    }
};
```
