## 148. Sort List - 排序链表

<!--If you want to use the English description, use `question.content` instead-->

<p>在&nbsp;<em>O</em>(<em>n</em>&nbsp;log&nbsp;<em>n</em>) 时间复杂度和常数级空间复杂度下，对链表进行排序。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 4-&gt;2-&gt;1-&gt;3
<strong>输出:</strong> 1-&gt;2-&gt;3-&gt;4
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> -1-&gt;5-&gt;3-&gt;4-&gt;0
<strong>输出:</strong> -1-&gt;0-&gt;3-&gt;4-&gt;5</pre>



-----

题目标签：Sort / Linked List

题目链接：[LeetCode](https://leetcode.com/problems/sort-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sort-list/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 44  ms | 22.5 MB |

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* sortList(ListNode* head) {
        if (!head || !head->next) return head;
        ListNode* t; ListNode* p; ListNode* q; ListNode* res;
        if (!head->next->next) {
            if ((t = head->next)->val < head->val) {
                t->next = head;
                head->next = NULL;
                return t;
            } else return head;
        }
        p = q = head;
        while (q->next && q->next->next) {
            p = p->next;
            q = q->next->next;
        }
        q = p->next;
        p->next = NULL;
        p = sortList(head);
        q = sortList(q);
        res = t = new ListNode(-1);
        while (p || q) {
            if (p && q) {
                if (p->val < q->val) {
                    t = t->next = p;
                    p = p->next;
                } else {
                    t = t->next = q;
                    q = q->next;
                }
            } else {
                t->next = p ? p : q;
                break;
            }
        }
        return res->next;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 3  ms | 40.4 MB |

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode sortList(ListNode head) {
        // 空节点或只有一个节点
        if (head == null || head.next == null) return head;
        // 只有两个节点
        if (head.next.next == null) {
            if (head.val > head.next.val) {
                ListNode p = head.next;
                head.next = null;
                p.next = head;
                head = p;
            }
            return head;
        }
        // 其余情况，分治
        ListNode p = head, q = head;
        while (q.next != null && q.next.next != null) {
            p = p.next;
            q = q.next.next;
        }
        ListNode rhead = p.next;
        p.next = null;
        ListNode l = sortList(head);
        ListNode r = sortList(rhead);
        // 归并
        ListNode dummy = new ListNode(-1);
        ListNode t = dummy;
        while (l != null || r != null) {
            if (l != null && r != null) {
                if (l.val > r.val) {
                    t.next = r;
                    r = r.next;
                } else {
                    t.next = l;
                    l = l.next; 
                }
                t = t.next;
                t.next = null;
            } else {
                t.next = l != null ? l : r;
                break;
            }
        }
        return dummy.next;
    }
}
```
