## 530. Minimum Absolute Difference in BST - 二叉搜索树的最小绝对差

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个所有节点为非负值的二叉搜索树，求树中任意两节点的差的绝对值的最小值。</p>

<p><strong>示例 :</strong></p>

<pre>
<strong>输入:</strong>

   1
    \
     3
    /
   2

<strong>输出:</strong>
1

<strong>解释:
</strong>最小绝对差为1，其中 2 和 1 的差的绝对值为 1（或者 2 和 3）。
</pre>

<p><strong>注意: </strong>树中至少有2个节点。</p>



-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/minimum-absolute-difference-in-bst/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-absolute-difference-in-bst/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 16  ms | 22.4 MB |

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
    vector<int> arr;
    void dfs(TreeNode* root) {
        if (!root) return;
        if (root->left) dfs(root->left);
        arr.push_back(root->val);
        if (root->right) dfs(root->right);
    }

    int getMinimumDifference(TreeNode* root) {
        dfs(root);
        int res = INT_MAX;
        for (int i = 1; i < (int)arr.size(); i++)
            res = min(res, arr[i] - arr[i - 1]);
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
