## 98. Validate Binary Search Tree - 验证二叉搜索树

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，判断其是否是一个有效的二叉搜索树。</p>

<p>假设一个二叉搜索树具有如下特征：</p>

<ul>
	<li>节点的左子树只包含<strong>小于</strong>当前节点的数。</li>
	<li>节点的右子树只包含<strong>大于</strong>当前节点的数。</li>
	<li>所有左子树和右子树自身必须也是二叉搜索树。</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong>
    2
   / \
  1   3
<strong>输出:</strong> true
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:
</strong>    5
   / \
  1   4
&nbsp;    / \
&nbsp;   3   6
<strong>输出:</strong> false
<strong>解释:</strong> 输入为: [5,1,4,null,null,3,6]。
&nbsp;    根节点的值为 5 ，但是其右子节点值为 4 。
</pre>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/validate-binary-search-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/validate-binary-search-tree/description/)

## 题解

注意BST的定义，根节点比左子树所有节点大，比右子树所有节点小，而不是只和子节点比较。

BST重要性质：中序遍历数组是升序的。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1.9 MB |

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
static auto _ = [](){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    void inorder(TreeNode* node, bool& res, int*& last) {
        if (!res) {
            return;
        }
        // cout << "[In] " << node->val << "  " << res << endl;
        if (node->left) {
            inorder(node->left, res, last);
        }

        if (last == nullptr || node->val > *last) {
            last = &(node->val);
        } else {
            res = false;
        }

        if (node->right) {
            inorder(node->right, res, last);
        }
        // cout << "[Out] " << node->val << "  " << res << endl;
    }

    bool isValidBST(TreeNode* root) {
        if (!root) { return true; }
        bool res = true;
        int* last = nullptr;
        inorder(root, res, last);
        // cout << "res: " << res << endl;
        return res;
    }
};
```
