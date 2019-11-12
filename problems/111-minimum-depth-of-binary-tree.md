## 111. Minimum Depth of Binary Tree - 二叉树的最小深度

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，找出其最小深度。</p>

<p>最小深度是从根节点到最近叶子节点的最短路径上的节点数量。</p>

<p><strong>说明:</strong>&nbsp;叶子节点是指没有子节点的节点。</p>

<p><strong>示例:</strong></p>

<p>给定二叉树&nbsp;<code>[3,9,20,null,null,15,7]</code>,</p>

<pre>    3
   / \
  9  20
    /  \
   15   7</pre>

<p>返回它的最小深度 &nbsp;2.</p>



-----

题目标签：Tree / Depth-first Search / Breadth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/minimum-depth-of-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-depth-of-binary-tree/description/)

## 题解

由于求的是最小深度，因此考虑层次遍历，注意层次遍历的写法。

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
public:
    int minDepth(TreeNode* root) {
        if(!root){
            return 0;
        }
        queue<TreeNode*> seq;
        unordered_set<TreeNode*> vt;
        vt.insert(root);
        seq.push(root);
        int res = 0;
        while(!seq.empty()){
            int cnt = seq.size();
            res++;
            // 层次遍历。注意写法！
            while(cnt--){
                TreeNode* node = seq.front();
                seq.pop();
                if(!node->left && !node->right){
                    return res;  // 当是叶子节点时，立即返回
                }
                if(node->left && !vt.count(node->left)){
                    vt.insert(node->left);
                    seq.push(node->left);
                }
                if(node->right && !vt.count(node->right)){
                    vt.insert(node->right);
                    seq.push(node->right);
                }
            }
        }
    }
};
```
