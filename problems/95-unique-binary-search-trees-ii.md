## 95. Unique Binary Search Trees II - 不同的二叉搜索树 II

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数 <em>n</em>，生成所有由 1 ...&nbsp;<em>n</em> 为节点所组成的<strong>二叉搜索树</strong>。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 3
<strong>输出:</strong>
[
&nbsp; [1,null,3,2],
&nbsp; [3,2,null,1],
&nbsp; [3,1,null,null,2],
&nbsp; [2,1,3],
&nbsp; [1,null,2,null,3]
]
<strong>解释:</strong>
以上的输出对应以下 5 种不同结构的二叉搜索树：

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
</pre>



-----

题目标签：Tree / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/unique-binary-search-trees-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/unique-binary-search-trees-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 20  ms | 1.4 MB |

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
    void backTracking(int l, int r, vector<TreeNode*>& ret) {
        if (l > r) {
            ret.emplace_back(nullptr);
            return;
        }
        if (l == r) {
            TreeNode* tmp = new TreeNode(l);
            ret.emplace_back(tmp);
            return;
        }
        for (int m=l; m<=r; ++m) {
            vector<TreeNode*> left;
            backTracking(l, m-1, left);
            vector<TreeNode*> right;
            backTracking(m+1, r, right);
            for (auto lt : left) {
                for (auto rt : right) {
                    TreeNode* root = new TreeNode(m);
                    root->left = lt;
                    root->right = rt;
                    ret.emplace_back(root);
                }
            }
        }
    }
    
    vector<TreeNode*> generateTrees(int n) {
        vector<TreeNode*> ret;
        if (n == 0) { return ret; }
        backTracking(1, n, ret);
        return ret;
    }
};
```
