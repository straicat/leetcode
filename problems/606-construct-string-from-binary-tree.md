## 606. Construct String from Binary Tree - 根据二叉树创建字符串

<!--If you want to use the English description, use `question.content` instead-->

<p>你需要采用前序遍历的方式，将一个二叉树转换成一个由括号和整数组成的字符串。</p>

<p>空节点则用一对空括号 &quot;()&quot; 表示。而且你需要省略所有不影响字符串与原始二叉树之间的一对一映射关系的空括号对。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> 二叉树: [1,2,3,4]
       1
     /   \
    2     3
   /    
  4     

<strong>输出:</strong> &quot;1(2(4))(3)&quot;

<strong>解释:</strong> 原本将是&ldquo;1(2(4)())(3())&rdquo;，
在你省略所有不必要的空括号对之后，
它将是&ldquo;1(2(4))(3)&rdquo;。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> 二叉树: [1,2,3,null,4]
       1
     /   \
    2     3
     \  
      4 

<strong>输出:</strong> &quot;1(2()(4))(3)&quot;

<strong>解释:</strong> 和第一个示例相似，
除了我们不能省略第一个对括号来中断输入和输出之间的一对一映射关系。
</pre>



-----

题目标签：Tree / String

题目链接：[LeetCode](https://leetcode.com/problems/construct-string-from-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/construct-string-from-binary-tree/description/)

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
    string res;
    void dfs(TreeNode* node){
        if(!node){
            return;
        }
        if(!res.empty()){
            res += "(";
        }
        res += to_string(node->val);
        if(node->left){
            dfs(node->left);
            res += ")";
        }else if(node->right){
            res += "()";
        }
        if(node->right){
            dfs(node->right);
            res += ")";
        }
    }
    string tree2str(TreeNode* t) {
        dfs(t);
        return res;
    }
};
```
