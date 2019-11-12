## 21. Merge Two Sorted Lists - 合并两个有序链表

<!--If you want to use the English description, use `question.content` instead-->

<p>将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>1-&gt;2-&gt;4, 1-&gt;3-&gt;4
<strong>输出：</strong>1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4
</pre>



-----

题目标签：Linked List

题目链接：[LeetCode](https://leetcode.com/problems/merge-two-sorted-lists/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/merge-two-sorted-lists/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 12  ms | 1.9 MB |

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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* res = new ListNode(-1);
        ListNode* r = res;
        ListNode* p = l1;
        ListNode* q = l2;
        while (p && q) {
            if (p->val < q->val) {
                r->next = new ListNode(p->val);
                p = p->next;
            } else {
                r->next = new ListNode(q->val);
                q = q->next;
            }
            r = r->next;
        }
        while (p) {
            r->next = new ListNode(p->val);
            p = p->next;
            r = r->next;
        }
        while (q) {
            r->next = new ListNode(q->val);
            q = q->next;
            r = r->next;
        }
        res = res->next;
        return res;
    }
};
```
