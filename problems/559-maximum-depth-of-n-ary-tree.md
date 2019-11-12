## 559. Maximum Depth of N-ary Tree - N叉树的最大深度

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个 N 叉树，找到其最大深度。</p>

<p>最大深度是指从根节点到最远叶子节点的最长路径上的节点总数。</p>

<p>例如，给定一个&nbsp;<code>3叉树</code>&nbsp;:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;"></p>

<p>&nbsp;</p>

<p>我们应返回其最大深度，3。</p>

<p><strong>说明:</strong></p>

<ol>
	<li>树的深度不会超过&nbsp;<code>1000</code>。</li>
	<li>树的节点总不会超过&nbsp;<code>5000</code>。</li>
</ol>


-----

题目标签：Tree / Depth-first Search / Breadth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/maximum-depth-of-n-ary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-depth-of-n-ary-tree/description/)

## 题解

递归地计算一个节点的左右子树的树高，将高度设值为两个孩子最大高度加1。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 92  ms | N/A |

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
    int maxDepth(Node* root) {
        if(!root) return 0;
        int h = 0;
        for(Node* child : root->children){
            h = max(h, maxDepth(child));
        }
        return h + 1;
    }
};
```
