## 206. Reverse Linked List - 反转链表

<!--If you want to use the English description, use `question.content` instead-->

<p>反转一个单链表。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL
<strong>输出:</strong> 5-&gt;4-&gt;3-&gt;2-&gt;1-&gt;NULL</pre>

<p><strong>进阶:</strong><br>
你可以迭代或递归地反转链表。你能否用两种方法解决这道题？</p>



-----

题目标签：Linked List

题目链接：[LeetCode](https://leetcode.com/problems/reverse-linked-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-linked-list/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 1.2 MB |

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
    ListNode* reverseList(ListNode* head) {
        if (!head || !head->next) { return head; }
        ListNode* p = head;
        ListNode* q = head->next;
        while (q->next) {
            ListNode* r = q->next;
            q->next = p;
            p = q;
            q = r;
        }
        q->next = p;
        head->next = NULL;
        return q;
    }
};
```
