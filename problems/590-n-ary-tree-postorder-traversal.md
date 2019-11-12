## 590. N-ary Tree Postorder Traversal - N叉树的后序遍历

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个 N 叉树，返回其节点值的<em>后序遍历</em>。</p>

<p>例如，给定一个&nbsp;<code>3叉树</code>&nbsp;:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;"></p>

<p>&nbsp;</p>

<p>返回其后序遍历: <code>[5,6,3,2,4,1]</code>.</p>

<p>&nbsp;</p>

<p><strong>说明:</strong>&nbsp;递归法很简单，你可以使用迭代法完成此题吗?</p>


-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/n-ary-tree-postorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/n-ary-tree-postorder-traversal/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 56  ms | N/A |

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
public:
    vector<int> postorder(Node* root) {
        vector<int> res;
        fs(root, &res);
        return res;
    }
    void fs(Node* cur, vector<int> *res){
        if(cur == NULL)
            return;
        for(Node* child : cur->children)
            fs(child, res);
        res->push_back(cur->val);
    }
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python  | 136  ms | N/A |

```python
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val, children):
        self.val = val
        self.children = children
"""
class Solution(object):
    def postorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        res = []
        def fs(r):
            if r is not None:
                for child in r.children:
                    fs(child)
                res.append(r.val)
        fs(root)
        return res
```
