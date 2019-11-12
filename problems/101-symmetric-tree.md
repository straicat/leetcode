## 101. Symmetric Tree - 对称二叉树

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，检查它是否是镜像对称的。</p>

<p>例如，二叉树&nbsp;<code>[1,2,2,3,4,4,3]</code> 是对称的。</p>

<pre>    1
   / \
  2   2
 / \ / \
3  4 4  3
</pre>

<p>但是下面这个&nbsp;<code>[1,2,2,null,3,null,3]</code> 则不是镜像对称的:</p>

<pre>    1
   / \
  2   2
   \   \
   3    3
</pre>

<p><strong>说明:</strong></p>

<p>如果你可以运用递归和迭代两种方法解决这个问题，会很加分。</p>



-----

题目标签：Tree / Depth-first Search / Breadth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/symmetric-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/symmetric-tree/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | N/A |

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
private:
    bool isSymmetricNode(TreeNode* left, TreeNode* right){
        if(!left && !right)
            return true;
        if(!left || !right || left->val != right->val)
            return false;
        return isSymmetricNode(left->left, right->right) && isSymmetricNode(left->right, right->left);
}
public:
    bool isSymmetric(TreeNode* root) {
        if(!root)
            return true;
        return isSymmetricNode(root->left, root->right);
    }
};
```
