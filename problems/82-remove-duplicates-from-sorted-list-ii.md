## 82. Remove Duplicates from Sorted List II - 删除排序链表中的重复元素 II

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个排序链表，删除所有含有重复数字的节点，只保留原始链表中&nbsp;<em>没有重复出现&nbsp;</em>的数字。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> 1-&gt;2-&gt;3-&gt;3-&gt;4-&gt;4-&gt;5
<strong>输出:</strong> 1-&gt;2-&gt;5
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> 1-&gt;1-&gt;1-&gt;2-&gt;3
<strong>输出:</strong> 2-&gt;3</pre>



-----

题目标签：Linked List

题目链接：[LeetCode](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1.3 MB |

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
static auto _ = [](){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if (!head || !head->next) { return head; }
        ListNode* g = new ListNode(0);
        g->next = head;
        ListNode* p = g;
        ListNode* q = head->next;
        while (q) {
            if (q->val == p->next->val) {
                q = q->next;
            } else {
                if (p->next->next != q) {
                    p->next = q;
                } else {
                    p = p->next;
                }
                q = q->next;
            }
        }
        if (p->next->next != q) {
            p->next = q;
        }
        return g->next;
    }
};
```
