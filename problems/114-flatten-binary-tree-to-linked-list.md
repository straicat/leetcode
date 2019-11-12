## 114. Flatten Binary Tree to Linked List - 二叉树展开为链表

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，<a href="https://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95/8010757" target="_blank">原地</a>将它展开为链表。</p>

<p>例如，给定二叉树</p>

<pre>    1
   / \
  2   5
 / \   \
3   4   6</pre>

<p>将其展开为：</p>

<pre>1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6</pre>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/flatten-binary-tree-to-linked-list/description/)

## 题解

过程形象描述为：把右子树取下来，把左子树取下来放到右边并链表化，再把取下来的右子树放到链表的尾部并链表化。有个关键在于，我们要知道链表的尾部，因此，递归函数返回链表尾部。

如果是叶子节点，直接返回该节点；如果只有左子树，就只需把左子树取下来放到右边并链表化；如果只有右子树，就只需把右子树链表化。

注意空指针，不仅在递归里需要考虑，根节点是否为空指针也要考虑。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | N/A |

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
    TreeNode* flattenSub(TreeNode* root){
        if(root->left && root->right){
            TreeNode* tmp = root->right;
            root->right = root->left;
            root->left = NULL;
            TreeNode* ed = flattenSub(root->right);
            ed->right = tmp;
            return flattenSub(tmp);
        }else{
            if(root->left){
                root->right = root->left;
                root->left = NULL;
                return flattenSub(root->right);
            }
            if(root->right){
                return flattenSub(root->right);
            }
            return root;
        }
    }
    void flatten(TreeNode* root) {
        if(root){
            flattenSub(root);
        }
    }
};
```
