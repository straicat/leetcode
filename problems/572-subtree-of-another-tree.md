## 572. Subtree of Another Tree - 另一个树的子树

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个非空二叉树 <strong>s</strong> 和 <strong>t</strong>，检验&nbsp;<strong>s</strong> 中是否包含和 <strong>t</strong> 具有相同结构和节点值的子树。<strong>s</strong> 的一个子树包括 <strong>s</strong> 的一个节点和这个节点的所有子孙。<strong>s</strong> 也可以看做它自身的一棵子树。</p>

<p><strong>示例 1:</strong><br />
给定的树 s:</p>

<pre>
     3
    / \
   4   5
  / \
 1   2
</pre>

<p>给定的树 t：</p>

<pre>
   4 
  / \
 1   2
</pre>

<p>返回 <strong>true</strong>，因为 t 与 s 的一个子树拥有相同的结构和节点值。</p>

<p><strong>示例 2:</strong><br />
给定的树 s：</p>

<pre>
     3
    / \
   4   5
  / \
 1   2
    /
   0
</pre>

<p>给定的树 t：</p>

<pre>
   4
  / \
 1   2
</pre>

<p>返回 <strong>false</strong>。</p>



-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/subtree-of-another-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/subtree-of-another-tree/description/)

## 题解

这题有利于理解递归。判定两个树相同，就是判断根节点相同，且其子树相同，这是递归。判定树A是树B的子树，就是判断树A和树B是否相同，如果相同，则是子树；如果不同，就判断树B的子树是否有和树A相同的，这也是个递归的过程。

本题采用两个递归+空指针判断即可。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 12  ms | N/A |

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
    bool isSametree(TreeNode* t1, TreeNode* t2){
        if(!t1 && !t2){
            return true;
        }
        if(!t1 || !t2){
            return false;
        }
        if(t1->val == t2->val){
            return isSametree(t1->left, t2->left) && isSametree(t1->right, t2->right);
        }else{
            return false;
        }
    }
    bool isSubtree(TreeNode* s, TreeNode* t) {
        if(!s && !t){
            return true;
        }
        if(!s || !t){
            return false;
        }
        if(isSametree(s, t)){
            return true;
        }
        return isSubtree(s->left, t) || isSubtree(s->right, t);
    }
};
```
