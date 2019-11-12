## 430. Flatten a Multilevel Doubly Linked List - 扁平化多级双向链表

<!--If you want to use the English description, use `question.content` instead-->

<p>您将获得一个双向链表，除了下一个和前一个指针之外，它还有一个子指针，可能指向单独的双向链表。这些子列表可能有一个或多个自己的子项，依此类推，生成多级数据结构，如下面的示例所示。</p>

<p>扁平化列表，使所有结点出现在单级双链表中。您将获得列表第一级的头部。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>
 1---2---3---4---5---6--NULL
         |
         7---8---9---10--NULL
             |
             11--12--NULL

<strong>输出:</strong>
1-2-3-7-8-11-12-9-10-4-5-6-NULL
</pre>

<p>&nbsp;</p>

<p><strong>以上示例的说明:</strong></p>

<p>给出以下多级双向链表:</p>

<pre><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/multilevellinkedlist.png" style="width: 640px;"></pre>

<p>&nbsp;</p>

<p>我们应该返回如下所示的扁平双向链表:</p>

<pre><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/multilevellinkedlistflattened.png" style="width: 1100px;"></pre>



-----

题目标签：Depth-first Search / Linked List

题目链接：[LeetCode](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/flatten-a-multilevel-doubly-linked-list/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 0  ms | 37 MB |

```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node prev;
    public Node next;
    public Node child;

    public Node() {}

    public Node(int _val,Node _prev,Node _next,Node _child) {
        val = _val;
        prev = _prev;
        next = _next;
        child = _child;
    }
};
*/
class Solution {
    public Node flatten(Node head) {
        Node p = head;
        while (p != null) {
            // 如果没有child，直接到next节点
            if (p.child == null) {
                p = p.next;
            } else {
                // 如果有child，先递归地扁平化child节点
                Node t = flatten(p.child);
                // 然后处理当前节点与扁平化后的child节点的指针
                Node q = p.next;
                p.next = t;
                // child和prev指针不要忘记处理了
                p.child = null;
                t.prev = p;
                while (p.next != null) {
                    p = p.next;
                }
                p.next = q;
                // 扁平化后的child节点后面的节点的prev指针也需要修改
                // q可能为null。当p为最后一个节点时，q为null，需要判断一下
                if (q != null)
                    q.prev = p;
                p = q;
            }
        }
        return head;
    }
}
```
