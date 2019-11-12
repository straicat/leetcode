## 106. Construct Binary Tree from Inorder and Postorder Traversal - 从中序与后序遍历序列构造二叉树

<!--If you want to use the English description, use `question.content` instead-->

<p>根据一棵树的中序遍历与后序遍历构造二叉树。</p>

<p><strong>注意:</strong><br>
你可以假设树中没有重复的元素。</p>

<p>例如，给出</p>

<pre>中序遍历 inorder =&nbsp;[9,3,15,20,7]
后序遍历 postorder = [9,15,7,20,3]</pre>

<p>返回如下的二叉树：</p>

<pre>    3
   / \
  9  20
    /  \
   15   7
</pre>



-----

题目标签：Tree / Depth-first Search / Array

题目链接：[LeetCode](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 16  ms | 1.3 MB |

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
    void build(vector<int>& in, vector<int>& post, int il, int ir, int pl, int pr, TreeNode*& ret) {
        if (il >= ir || pl >= pr) {
            return;
        }
        ret = new TreeNode(post[pr-1]);
        int x = 0;
        for (int i=il; i<ir; ++i) {
            if (in[i] == post[pr-1]) {
                x = i - il;
                break;
            }
        }
        build(in, post, il+x+1, ir, pl+x, pr-1, ret->right);
        build(in, post, il, il+x, pl, pl+x, ret->left);
    }
    
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        TreeNode* root = nullptr;
        build(inorder, postorder, 0, inorder.size(), 0, postorder.size(), root);
        return root;
    }
};
```
