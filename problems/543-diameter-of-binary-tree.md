## 543. Diameter of Binary Tree - 二叉树的直径

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一棵二叉树，你需要计算它的直径长度。一棵二叉树的直径长度是任意两个结点路径长度中的最大值。这条路径可能穿过根结点。</p>

<p><strong>示例 :</strong><br />
给定二叉树</p>

<pre>
          1
         / \
        2   3
       / \     
      4   5    
</pre>

<p>返回&nbsp;<strong>3</strong>, 它的长度是路径 [4,2,1,3] 或者&nbsp;[5,2,1,3]。</p>

<p><strong>注意：</strong>两结点之间的路径长度是以它们之间边的数目表示。</p>



-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/diameter-of-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/diameter-of-binary-tree/description/)

## 题解



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
    vector<int> tmp;
    int maxDepth(TreeNode* node){
        if(!node){
            return 0;
        }
        int l = maxDepth(node->left);
        int r = maxDepth(node->right);
        tmp.push_back(l + r);
        return 1 + max(l, r);
    }
    int diameterOfBinaryTree(TreeNode* root) {
        if(!root){
            return 0;
        }
        maxDepth(root);
        return *max_element(tmp.begin(), tmp.end());
    }
};
```
