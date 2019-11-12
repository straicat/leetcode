## 110. Balanced Binary Tree - 平衡二叉树

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，判断它是否是高度平衡的二叉树。</p>

<p>本题中，一棵高度平衡二叉树定义为：</p>

<blockquote>
<p>一个二叉树<em>每个节点&nbsp;</em>的左右两个子树的高度差的绝对值不超过1。</p>
</blockquote>

<p><strong>示例 1:</strong></p>

<p>给定二叉树 <code>[3,9,20,null,null,15,7]</code></p>

<pre>    3
   / \
  9  20
    /  \
   15   7</pre>

<p>返回 <code>true</code> 。<br>
<br>
<strong>示例 2:</strong></p>

<p>给定二叉树 <code>[1,2,2,3,3,null,null,4,4]</code></p>

<pre>       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
</pre>

<p>返回&nbsp;<code>false</code> 。</p>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/balanced-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/balanced-binary-tree/description/)

## 题解

注意是**每个**节点都要求子树高度差不超过1，所以，不能只判断根节点，还要判断子节点，可以使用递归。判断高度差就是取子树的最大高度+1。注意空指针判断。递归注意出口条件。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 1  ms | 40.5 MB |

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    private int depth(TreeNode node) {
        if (node == null) return 0;
        return 1 + Math.max(depth(node.left), depth(node.right));
    }
    public boolean isBalanced(TreeNode root) {
        if (root == null) return true;
        if (Math.abs(depth(root.left) - depth(root.right)) > 1) return false;
        return isBalanced(root.left) && isBalanced(root.right);
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | N/A |

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
    int maxDepth(TreeNode* node){
        if(!node){
            return 0;
        }
        return 1 + max(maxDepth(node->left), maxDepth(node->right));
    }
    bool isBalanced(TreeNode* root) {
        if(!root){
            return true;
        }
        // 某个节点不平衡，则整棵树不平衡，立即返回false
        if(abs(maxDepth(root->left) - maxDepth(root->right)) > 1){
            return false;
        }else{
            // 递归判断子节点是否都平衡
            return isBalanced(root->left) && isBalanced(root->right);
        }
    }
};
```
