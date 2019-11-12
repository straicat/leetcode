## 105. Construct Binary Tree from Preorder and Inorder Traversal - 从前序与中序遍历序列构造二叉树

<!--If you want to use the English description, use `question.content` instead-->

<p>根据一棵树的前序遍历与中序遍历构造二叉树。</p>

<p><strong>注意:</strong><br>
你可以假设树中没有重复的元素。</p>

<p>例如，给出</p>

<pre>前序遍历 preorder =&nbsp;[3,9,20,15,7]
中序遍历 inorder = [9,3,15,20,7]</pre>

<p>返回如下的二叉树：</p>

<pre>    3
   / \
  9  20
    /  \
   15   7</pre>



-----

题目标签：Tree / Depth-first Search / Array

题目链接：[LeetCode](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)

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
    void build(vector<int>& pre, vector<int>& in, int pl, int pr, int il, int ir, TreeNode*& ret) {
        
        if (il >= ir || pl >= pr) {
            return;
        }
        // cout << "[In] " << pl << ", " << pr << "    " << il << ", " << ir << endl;
        ret = new TreeNode(pre[pl]);
        int x = 0;
        for (int i=il; i<ir; ++i) {
            if (in[i] == pre[pl]) {
                x = i - il;
                break;
            }
        }
        build(pre, in, pl+1, pl+1+x, il, il+x, ret->left);
        build(pre, in, pl+1+x, pr, il+x+1, ir, ret->right);
    }
    
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        TreeNode* root = nullptr;
        build(preorder, inorder, 0, preorder.size(), 0, inorder.size(), root);
        return root;
    }
};
```
