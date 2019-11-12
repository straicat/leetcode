## 234. Palindrome Linked List - 回文链表

<!--If you want to use the English description, use `question.content` instead-->

<p>请判断一个链表是否为回文链表。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2
<strong>输出:</strong> false</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;2-&gt;1
<strong>输出:</strong> true
</pre>

<p><strong>进阶：</strong><br>
你能否用&nbsp;O(n) 时间复杂度和 O(1) 空间复杂度解决此题？</p>



-----

题目标签：Linked List / Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/palindrome-linked-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/palindrome-linked-list/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 4.5 MB |

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
    bool isPalindrome(ListNode* head) {
        if (head == NULL || head->next == NULL) {
            return true;
        }
        ListNode* dummy = new ListNode(0);
        dummy->next = head;
        ListNode* p = dummy;
        ListNode* q = head;
        while (q && q->next) {
            p = p->next;
            q = q->next->next;
        }

        ListNode* r = p->next;
        ListNode* s = r->next;
        if (s == NULL) {
            return p->val == r->val;
        }
        ListNode* t = s->next;
        p->next = NULL;
        r->next = NULL;
        while (true) {
            s->next = r;
            r = s;
            s = t;
            if (t == NULL) {
                break;
            } else {
                t = t->next;
            }
        }
        if (q == NULL) {
            q = r;
        }

        p = head;
        while (p != NULL && q != NULL) {
            if (p->val != q->val) {
                return false;
            }
            p = p->next;
            q = q->next;
        }
        return true;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
