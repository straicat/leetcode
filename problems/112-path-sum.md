## 112. Path Sum - 路径总和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树和一个目标和，判断该树中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。</p>

<p><strong>说明:</strong>&nbsp;叶子节点是指没有子节点的节点。</p>

<p><strong>示例:</strong>&nbsp;<br>
给定如下二叉树，以及目标和 <code>sum = 22</code>，</p>

<pre>              <strong>5</strong>
             / \
            <strong>4 </strong>  8
           /   / \
          <strong>11 </strong> 13  4
         /  \      \
        7    <strong>2</strong>      1
</pre>

<p>返回 <code>true</code>, 因为存在目标和为 22 的根节点到叶子节点的路径 <code>5-&gt;4-&gt;11-&gt;2</code>。</p>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/path-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/path-sum/description/)

## 题解

判断是否存在，因此可以考虑DFS。需要记录经过的节点的值，每次访问新节点就加入节点值，从栈中退出就移除加入的节点值。当访问叶节点时，对路径节点值求和做判断。

在递归时需要注意，当递归返回true时，说明找到了符合条件的路径，可以立即返回true。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1.3 MB |

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
    vector<int> path;
    bool hasPathSum(TreeNode* root, int sum) {
        if(!root){
            return false;
        }
        path.push_back(root->val);  // add node to path
        if(!root->left && !root->right){
            if(accumulate(path.begin(), path.end(), 0) == sum){
                return true;
            }
        }
        if(root->left){
            if(hasPathSum(root->left, sum)){
                return true;
            }
            path.pop_back();  // pop from stack, remove node from path
        }
        if(root->right){
            if(hasPathSum(root->right, sum)){
                return true;
            }
            path.pop_back();  // pop from stack, remove node from path
        }
        return false;
    }
};
```
