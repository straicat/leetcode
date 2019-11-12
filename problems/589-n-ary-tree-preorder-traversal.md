## 589. N-ary Tree Preorder Traversal - N叉树的前序遍历

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个 N 叉树，返回其节点值的<em>前序遍历</em>。</p>

<p>例如，给定一个&nbsp;<code>3叉树</code>&nbsp;:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;"></p>

<p>&nbsp;</p>

<p>返回其前序遍历: <code>[1,3,5,6,2,4]</code>。</p>

<p>&nbsp;</p>

<p><strong>说明:&nbsp;</strong>递归法很简单，你可以使用迭代法完成此题吗?</p>


-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/n-ary-tree-preorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/n-ary-tree-preorder-traversal/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 80  ms | N/A |

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> children;

    Node() {}

    Node(int _val, vector<Node*> _children) {
        val = _val;
        children = _children;
    }
};
*/
class Solution {
private:
    void preorderProcess(Node* cur, vector<int>& res){
        if(!cur) return;
        res.push_back(cur->val);
        for(Node* child : cur->children)
            preorderProcess(child, res);
    }
public:
    vector<int> preorder(Node* root) {
        vector<int> res;
        preorderProcess(root, res);
        return res;
    }
};
```
