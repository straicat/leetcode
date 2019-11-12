## 108. Convert Sorted Array to Binary Search Tree - 将有序数组转换为二叉搜索树

<!--If you want to use the English description, use `question.content` instead-->

<p>将一个按照升序排列的有序数组，转换为一棵高度平衡二叉搜索树。</p>

<p>本题中，一个高度平衡二叉树是指一个二叉树<em>每个节点&nbsp;</em>的左右两个子树的高度差的绝对值不超过 1。</p>

<p><strong>示例:</strong></p>

<pre>给定有序数组: [-10,-3,0,5,9],

一个可能的答案是：[0,-3,9,-10,null,5]，它可以表示下面这个高度平衡二叉搜索树：

      0
     / \
   -3   9
   /   /
 -10  5
</pre>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/convert-sorted-array-to-binary-search-tree/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | N/A |

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
    TreeNode* buildRoot(vector<int>& nums, int st, int ed){
        if(st>ed || st<0 || ed>=nums.size()){
            return nullptr;
        }else if(st==ed){
            return new TreeNode(nums[st]);
        }else{
            int mid = (st + ed) / 2;
            TreeNode* r = new TreeNode(nums[mid]);
            r->left = buildRoot(nums, st, mid-1);
            r->right = buildRoot(nums, mid+1, ed);
            return r;
        }
    }
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        return buildRoot(nums, 0, nums.size()-1);
    }
};
```
