## 257. Binary Tree Paths - 二叉树的所有路径

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树，返回所有从根节点到叶子节点的路径。</p>

<p><strong>说明:</strong>&nbsp;叶子节点是指没有子节点的节点。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>

   1
 /   \
2     3
 \
  5

<strong>输出:</strong> [&quot;1-&gt;2-&gt;5&quot;, &quot;1-&gt;3&quot;]

<strong>解释:</strong> 所有根节点到叶子节点的路径为: 1-&gt;2-&gt;5, 1-&gt;3</pre>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/binary-tree-paths/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-paths/description/)

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
    vector<string> res;
    vector<int> path;
    string join(vector<int>& p, string delimiter){
        stringstream ss;
        for(int i=0; i<p.size(); i++){
            if(i) { ss << delimiter; }
            ss << to_string(p[i]);
        }
        return ss.str();
    }
    void dfs(TreeNode* node){
        if(!node){
            return;
        }
        path.push_back(node->val);
        if(node->left){
            dfs(node->left);
            path.pop_back();
        }
        if(node->right){
            dfs(node->right);
            path.pop_back();
        }
        if(!node->left && !node->right){
            res.push_back(join(path, "->"));
        }
    }
    vector<string> binaryTreePaths(TreeNode* root) {
        dfs(root);
        return res;
    }
};
```
