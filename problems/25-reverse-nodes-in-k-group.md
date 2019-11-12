## 25. Reverse Nodes in k-Group - K 个一组翻转链表

<!--If you want to use the English description, use `question.content` instead-->

<p>给你一个链表，每&nbsp;<em>k&nbsp;</em>个节点一组进行翻转，请你返回翻转后的链表。</p>

<p><em>k&nbsp;</em>是一个正整数，它的值小于或等于链表的长度。</p>

<p>如果节点总数不是&nbsp;<em>k&nbsp;</em>的整数倍，那么请将最后剩余的节点保持原有顺序。</p>

<p><strong>示例 :</strong></p>

<p>给定这个链表：<code>1-&gt;2-&gt;3-&gt;4-&gt;5</code></p>

<p>当&nbsp;<em>k&nbsp;</em>= 2 时，应当返回: <code>2-&gt;1-&gt;4-&gt;3-&gt;5</code></p>

<p>当&nbsp;<em>k&nbsp;</em>= 3 时，应当返回: <code>3-&gt;2-&gt;1-&gt;4-&gt;5</code></p>

<p><strong>说明 :</strong></p>

<ul>
	<li>你的算法只能使用常数的额外空间。</li>
	<li><strong>你不能只是单纯的改变节点内部的值</strong>，而是需要实际的进行节点交换。</li>
</ul>



-----

题目标签：Linked List

题目链接：[LeetCode](https://leetcode.com/problems/reverse-nodes-in-k-group/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 36  ms | 1.3 MB |

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
static auto _ = []() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        if (k == 1) { return head; }
        ListNode* guard = new ListNode(0);
        guard->next = head;
        ListNode* cur = guard;
        bool stop = false;
        while (!stop) {
            // to see whether need to reverse
            ListNode* tmp = cur;
            for(int i=0; i<k; ++i) {
                tmp = tmp->next;
                if (!tmp) {
                    stop = true;
                    break;
                }
            }
            if (!stop) {
                ListNode* p = cur;
                ListNode* q = cur;
                // loop swap for a batch reverse
                for (int i=k-1; i>0; --i) {
                    p = cur;
                    q = cur->next;
                    for (int j=0; j<i; ++j) {
                        // a->b->c->d  -->  a->c->b->d
                        p->next = q->next;
                        q->next = q->next->next;
                        p->next->next = q;
                        p = p->next;
                    }
                }
                // point to next batch
                for (int i=0; i<k; ++i) {
                    cur = cur->next;
                }
            }
        }
        return guard->next;
    }
};
```
