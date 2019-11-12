## 86. Partition List - 分隔链表

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个链表和一个特定值<em> x</em>，对链表进行分隔，使得所有小于 <em>x</em> 的节点都在大于或等于 <em>x</em> 的节点之前。</p>

<p>你应当保留两个分区中每个节点的初始相对位置。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> head = 1-&gt;4-&gt;3-&gt;2-&gt;5-&gt;2, <em>x</em> = 3
<strong>输出:</strong> 1-&gt;2-&gt;2-&gt;4-&gt;3-&gt;5
</pre>



-----

题目标签：Linked List / Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/partition-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/partition-list/description/)

## 题解

正常来讲，应该通过调整链表的指针来实现，要考虑的细节比较多。一种比较取巧的方式是：遍历得到数组，然后排序，然后修改链表节点的值。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 68  ms | N/A |

```python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def partition(self, head, x):
        """
        :type head: ListNode
        :type x: int
        :rtype: ListNode
        """
        if head is None:
            return head
        it = head
        arr = []
        while it is not None:
            arr.append(it.val)
            it = it.next
        arr.sort(key=lambda _: _ >= x)
        it = head
        i = 0
        while it is not None:
            it.val = arr[i]
            it = it.next
            i += 1
        return head
```
