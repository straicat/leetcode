## 199. Binary Tree Right Side View - 二叉树的右视图

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一棵二叉树，想象自己站在它的右侧，按照从顶部到底部的顺序，返回从右侧所能看到的节点值。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>&nbsp;[1,2,3,null,5,null,4]
<strong>输出:</strong>&nbsp;[1, 3, 4]
<strong>解释:
</strong>
   1            &lt;---
 /   \
2     3         &lt;---
 \     \
  5     4       &lt;---
</pre>



-----

题目标签：Tree / Depth-first Search / Breadth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/binary-tree-right-side-view/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-right-side-view/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 856.1 KB |

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
    vector<int> rightSideView(TreeNode* root) {
        vector<int> res;
        if (!root) return res;
        queue<TreeNode*> Q;
        Q.push(root);
        while (!Q.empty()) {
            int n = Q.size();
            while (n--) {
                auto t = Q.front();
                if (n == 0) res.push_back(t->val);
                Q.pop();
                if (t->left) Q.push(t->left);
                if (t->right) Q.push(t->right);
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
