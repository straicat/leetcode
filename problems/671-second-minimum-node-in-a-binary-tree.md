## 671. Second Minimum Node In a Binary Tree - 二叉树中第二小的节点

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非空特殊的二叉树，每个节点都是正数，并且每个节点的子节点数量只能为&nbsp;<code>2</code>&nbsp;或&nbsp;<code>0</code>。如果一个节点有两个子节点的话，那么这个节点的值不大于它的子节点的值。&nbsp;</p>

<p>给出这样的一个二叉树，你需要输出所有节点中的<strong>第二小的值。</strong>如果第二小的值不存在的话，输出 -1 <strong>。</strong></p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> 
    2
   / \
  2   5
     / \
    5   7

<strong>输出:</strong> 5
<strong>说明:</strong> 最小的值是 2 ，第二小的值是 5 。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> 
    2
   / \
  2   2

<strong>输出:</strong> -1
<strong>说明:</strong> 最小的值是 2, 但是不存在第二小的值。
</pre>



-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/second-minimum-node-in-a-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/second-minimum-node-in-a-binary-tree/description/)

## 题解

C++里`set`的特点是：不重复，按元素大小存放。因此，可以把元素放在`set`里，然后利用迭代器取出第2个元素即可。

这题的二叉树比较特殊，本来考虑使用广度遍历，然后当`set`里元素不少于2个时就不继续，结果发现出错了！这个测试用例是：[1,1,3,1,1,3,4,3,1,1,1,3,8,4,8,3,3,1,6,2,1]。该测试用例的特点是：根与一个子节点相等，但是，第二小的元素位于该子节点的子树里，按照这种策略就会漏掉这种情况。

不考虑那么多，直接遍历，AC。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | N/A |

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
    int findSecondMinimumValue(TreeNode* root) {
        if(!root){
            return -1;
        }
        queue<TreeNode*> seq;
        set<TreeNode*> vt;
        set<int> nums;
        vt.insert(root);
        seq.push(root);
        while(!seq.empty()){
            TreeNode* node = seq.front();
            seq.pop();
            nums.insert(node->val);
            if(node->left && !vt.count(node->left)){
                vt.insert(node->left);
                seq.push(node->left);
            }
            if(node->right && !vt.count(node->right)){
                vt.insert(node->right);
                seq.push(node->right);
            }
        }
        if(nums.size() > 1){
            auto it = nums.begin();
            return *(next(it));
        }else{
            return -1;
        }
    }
};
```
