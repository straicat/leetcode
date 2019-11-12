## 637. Average of Levels in Binary Tree - 二叉树的层平均值

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非空二叉树, 返回一个由每层节点平均值组成的数组.</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong>
    3
   / \
  9  20
    /  \
   15   7
<strong>输出:</strong> [3, 14.5, 11]
<strong>解释:</strong>
第0层的平均值是 3,  第1层是 14.5, 第2层是 11. 因此返回 [3, 14.5, 11].
</pre>

<p><strong>注意：</strong></p>

<ol>
	<li>节点值的范围在32位有符号整数范围内。</li>
</ol>



-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/average-of-levels-in-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/average-of-levels-in-binary-tree/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 16  ms | N/A |

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
    vector<double> averageOfLevels(TreeNode* root) {
        vector<double> res;
        if(!root){
            return res;
        }
        queue<TreeNode*> seq;
        set<TreeNode*> visit;
        visit.insert(root);
        seq.push(root);
        while(!seq.empty()){
            int cnt = seq.size();
            int cntt = cnt;
            double sum = 0;
            while(cnt--){
                TreeNode* tmp = seq.front();
                seq.pop();
                if(tmp->left && !visit.count(tmp->left)){
                    visit.insert(tmp->left);
                    seq.push(tmp->left);
                }
                if(tmp->right && !visit.count(tmp->right)){
                    visit.insert(tmp->right);
                    seq.push(tmp->right);
                }
                sum += tmp->val;
            }
            res.push_back(sum / cntt);
        }
        return res;
    }
};
```
