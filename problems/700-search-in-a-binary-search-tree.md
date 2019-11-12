## 700. Search in a Binary Search Tree - 二叉搜索树中的搜索

<!--If you want to use the English description, use `question.content` instead-->

<p>给定二叉搜索树（BST）的根节点和一个值。 你需要在BST中找到节点值等于给定值的节点。 返回以该节点为根的子树。 如果节点不存在，则返回 NULL。</p>

<p>例如，</p>

<pre>
给定二叉搜索树:

        4
       / \
      2   7
     / \
    1   3

和值: 2
</pre>

<p>你应该返回如下子树:</p>

<pre>
      2     
     / \   
    1   3
</pre>

<p>在上述示例中，如果要找的值是 <code>5</code>，但因为没有节点值为 <code>5</code>，我们应该返回 <code>NULL</code>。</p>



-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/search-in-a-binary-search-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-in-a-binary-search-tree/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 92  ms | N/A |

```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def searchBST(self, root, val):
        """
        :type root: TreeNode
        :type val: int
        :rtype: TreeNode
        """
        if root is None:
            return None
        elif root.val == val:
            return root
        elif root.val < val:
            return self.searchBST(root.right, val)
        else:
            return self.searchBST(root.left, val)
```
