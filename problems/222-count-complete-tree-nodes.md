## 222. Count Complete Tree Nodes - 完全二叉树的节点个数

<!--If you want to use the English description, use `question.content` instead-->

<p>给出一个<strong>完全二叉树</strong>，求出该树的节点个数。</p>

<p><strong>说明：</strong></p>

<p><a href="https://baike.baidu.com/item/%E5%AE%8C%E5%85%A8%E4%BA%8C%E5%8F%89%E6%A0%91/7773232?fr=aladdin">完全二叉树</a>的定义如下：在完全二叉树中，除了最底层节点可能没填满外，其余每层节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。若最底层为第 h 层，则该层包含 1~&nbsp;2<sup>h</sup>&nbsp;个节点。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 
    1
   / \
  2   3
 / \  /
4  5 6

<strong>输出:</strong> 6</pre>



-----

题目标签：Tree / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/count-complete-tree-nodes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/count-complete-tree-nodes/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 36  ms | 28.5 MB |

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
    int countNodes(TreeNode* root) {
        if (!root) return 0;
        return 1 + countNodes(root->left) + countNodes(root->right);
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
