## 897. Increasing Order Search Tree - 递增顺序查找树

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个树，<strong>按中序遍历</strong>重新排列树，使树中最左边的结点现在是树的根，并且每个结点没有左子结点，只有一个右子结点。</p>

<p>&nbsp;</p>

<p><strong>示例 ：</strong></p>

<pre><strong>输入：</strong>[5,3,6,2,4,null,8,1,null,null,null,7,9]

       5
      / \
    3    6
   / \    \
  2   4    8
&nbsp;/        / \ 
1        7   9

<strong>输出：</strong>[1,null,2,null,3,null,4,null,5,null,6,null,7,null,8,null,9]

 1
&nbsp; \
&nbsp;  2
&nbsp;   \
&nbsp;    3
&nbsp;     \
&nbsp;      4
&nbsp;       \
&nbsp;        5
&nbsp;         \
&nbsp;          6
&nbsp;           \
&nbsp;            7
&nbsp;             \
&nbsp;              8
&nbsp;               \
                 9  </pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>给定树中的结点数介于 1 和&nbsp;100 之间。</li>
	<li>每个结点都有一个从 0 到 1000 范围内的唯一整数值。</li>
</ol>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/increasing-order-search-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/increasing-order-search-tree/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 164  ms | N/A |

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
    vector<int> rst;
    void dfs(TreeNode* cur){
        if(cur->left){
            dfs(cur->left);
        }
        cout << cur->val << endl;
        rst.push_back(cur->val);
        if(cur->right){
            dfs(cur->right);
        }
    }
    TreeNode* increasingBST(TreeNode* root) {
        if(!root){
            return root;
        }
        dfs(root);
        TreeNode* _root = root;
        root->left = NULL;
        root->right = NULL;
        root->val = rst[0];
        for(uint i=1; i<rst.size(); i++){
            TreeNode * tmp = new TreeNode(rst[i]);
            root->right = tmp;
            root = tmp;
        }
        return _root;
    }
};
```
