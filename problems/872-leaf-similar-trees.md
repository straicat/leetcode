## 872. Leaf-Similar Trees - 叶子相似的树

<!--If you want to use the English description, use `question.content` instead-->

<p>请考虑一颗二叉树上所有的叶子，这些叶子的值按从左到右的顺序排列形成一个&nbsp;<em>叶值序列</em> 。</p>

<p><img alt="" src="https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/16/tree.png" style="height: 240px; width: 300px;"></p>

<p>举个例子，如上图所示，给定一颗叶值序列为&nbsp;<code>(6, 7, 4, 9, 8)</code>&nbsp;的树。</p>

<p>如果有两颗二叉树的叶值序列是相同，那么我们就认为它们是&nbsp;<em>叶相似&nbsp;</em>的。</p>

<p>如果给定的两个头结点分别为&nbsp;<code>root1</code> 和&nbsp;<code>root2</code>&nbsp;的树是叶相似的，则返回&nbsp;<code>true</code>；否则返回 <code>false</code> 。</p>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>给定的两颗树可能会有&nbsp;<code>1</code>&nbsp;到&nbsp;<code>100</code>&nbsp;个结点。</li>
</ul>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/leaf-similar-trees/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/leaf-similar-trees/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | N/A |

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
    void leafSequence(TreeNode* cur, vector<int>& seq){
        if(!cur->left && !cur->right){
            seq.push_back(cur->val);
        }else{
            if(cur->left) {
                leafSequence(cur->left, seq);
            }
            if(cur->right) {
                leafSequence(cur->right, seq);
            }
        }
    }

    bool leafSimilar(TreeNode* root1, TreeNode* root2) {
        vector<int> seq1, seq2;
        leafSequence(root1, seq1);
        leafSequence(root2, seq2);
        if(seq1.size()!=seq2.size()){
            return false;
        }else{
            for(int i=0; i<seq1.size(); i++){
                if(seq1[i] != seq2[i]){
                    return false;
                }
            }
            return true;
        }
    }
};
```
