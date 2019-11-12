## 61. Rotate List - 旋转链表

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个链表，旋转链表，将链表每个节点向右移动&nbsp;<em>k&nbsp;</em>个位置，其中&nbsp;<em>k&nbsp;</em>是非负数。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL, k = 2
<strong>输出:</strong> 4-&gt;5-&gt;1-&gt;2-&gt;3-&gt;NULL
<strong>解释:</strong>
向右旋转 1 步: 5-&gt;1-&gt;2-&gt;3-&gt;4-&gt;NULL
向右旋转 2 步: 4-&gt;5-&gt;1-&gt;2-&gt;3-&gt;NULL
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> 0-&gt;1-&gt;2-&gt;NULL, k = 4
<strong>输出:</strong> <code>2-&gt;0-&gt;1-&gt;NULL</code>
<strong>解释:</strong>
向右旋转 1 步: 2-&gt;0-&gt;1-&gt;NULL
向右旋转 2 步: 1-&gt;2-&gt;0-&gt;NULL
向右旋转 3 步:&nbsp;<code>0-&gt;1-&gt;2-&gt;NULL</code>
向右旋转 4 步:&nbsp;<code>2-&gt;0-&gt;1-&gt;NULL</code></pre>



-----

题目标签：Linked List / Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/rotate-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/rotate-list/description/)

## 题解

比较简单的单链表题目，注意空链表！

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 48  ms | N/A |

```python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def rotateRight(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        nodes = []
        while head:
            nodes.append(head)
            head = head.next
        if nodes:
            k %= len(nodes)
            if k > 0:
                nodes[-1].next = nodes[0]
                nodes[len(nodes) - k - 1].next = None
            return nodes[-1 * k]
        else:
            return None
```
