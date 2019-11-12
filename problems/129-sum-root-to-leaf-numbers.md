## 129. Sum Root to Leaf Numbers - 求根到叶子节点数字之和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，它的每个结点都存放一个&nbsp;<code>0-9</code>&nbsp;的数字，每条从根到叶子节点的路径都代表一个数字。</p>

<p>例如，从根到叶子节点路径 <code>1-&gt;2-&gt;3</code> 代表数字 <code>123</code>。</p>

<p>计算从根到叶子节点生成的所有数字之和。</p>

<p><strong>说明:</strong>&nbsp;叶子节点是指没有子节点的节点。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,2,3]
    1
   / \
  2   3
<strong>输出:</strong> 25
<strong>解释:</strong>
从根到叶子节点路径 <code>1-&gt;2</code> 代表数字 <code>12</code>.
从根到叶子节点路径 <code>1-&gt;3</code> 代表数字 <code>13</code>.
因此，数字总和 = 12 + 13 = <code>25</code>.</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [4,9,0,5,1]
    4
   / \
  9   0
&nbsp;/ \
5   1
<strong>输出:</strong> 1026
<strong>解释:</strong>
从根到叶子节点路径 <code>4-&gt;9-&gt;5</code> 代表数字 495.
从根到叶子节点路径 <code>4-&gt;9-&gt;1</code> 代表数字 491.
从根到叶子节点路径 <code>4-&gt;0</code> 代表数字 40.
因此，数字总和 = 495 + 491 + 40 = <code>1026</code>.</pre>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/sum-root-to-leaf-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-root-to-leaf-numbers/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 950.3 KB |

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
    int res = 0;
    void dfs(TreeNode* node, vector<int>& path) {
        if (!node) {
            return;
        }
        path.push_back(node->val);
        if (!node->left && !node->right) {
            int k = 0;
            for (int i : path) {
                k = 10 * k + i;
            }
            cout << k << endl;
            res += k;
        }
        if (node->left) {
            dfs(node->left, path);
        }
        if (node->right) {
            dfs(node->right, path);
        }
        path.pop_back();
    }

    int sumNumbers(TreeNode* root) {
        vector<int> path;
        dfs(root, path);
        return res;
    }
};

static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
