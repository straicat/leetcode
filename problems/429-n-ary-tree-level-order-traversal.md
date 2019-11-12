## 429. N-ary Tree Level Order Traversal - N叉树的层序遍历

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个 N 叉树，返回其节点值的<em>层序遍历</em>。 (即从左到右，逐层遍历)。</p>

<p>例如，给定一个&nbsp;<code>3叉树</code>&nbsp;:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;"></p>

<p>&nbsp;</p>

<p>返回其层序遍历:</p>

<pre>[
     [1],
     [3,2,4],
     [5,6]
]
</pre>

<p>&nbsp;</p>

<p><strong>说明:</strong></p>

<ol>
	<li>树的深度不会超过&nbsp;<code>1000</code>。</li>
	<li>树的节点总数不会超过&nbsp;<code>5000</code>。</li>
</ol>


-----

题目标签：Tree / Breadth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/n-ary-tree-level-order-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/n-ary-tree-level-order-traversal/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 60  ms | N/A |

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val = NULL;
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
    vector<vector<int>> levelOrder(Node* root) {
        vector<vector<int>> res;
        if(!root){
            return res;
        }
        queue<Node*> seq;
        set<Node*> vt;
        vt.insert(root);
        seq.push(root);
        vector<int> row;
        row.push_back(root->val);
        res.push_back(row);
        while(!seq.empty()){
            int n = seq.size();
            vector<int> row;
            while(n--){
                Node* tmp = seq.front();
                seq.pop();
                for(Node* child : tmp->children){
                    if(!vt.count(child)){
                        vt.insert(child);
                        seq.push(child);
                        row.push_back(child->val);
                    }
                }
            }
            if(!row.empty()){
                res.push_back(row);
            }
        }
        return res;
    }
};
```
