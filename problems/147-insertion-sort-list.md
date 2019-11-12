## 147. Insertion Sort List - 对链表进行插入排序

<!--If you want to use the English description, use `question.content` instead-->

<p>对链表进行插入排序。</p>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif"><br>
<small>插入排序的动画演示如上。从第一个元素开始，该链表可以被认为已经部分排序（用黑色表示）。<br>
每次迭代时，从输入数据中移除一个元素（用红色表示），并原地将其插入到已排好序的链表中。</small></p>

<p>&nbsp;</p>

<p><strong>插入排序算法：</strong></p>

<ol>
	<li>插入排序是迭代的，每次只移动一个元素，直到所有元素可以形成一个有序的输出列表。</li>
	<li>每次迭代中，插入排序只从输入数据中移除一个待排序的元素，找到它在序列中适当的位置，并将其插入。</li>
	<li>重复直到所有输入数据插入完为止。</li>
</ol>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入:</strong> 4-&gt;2-&gt;1-&gt;3
<strong>输出:</strong> 1-&gt;2-&gt;3-&gt;4
</pre>

<p><strong>示例&nbsp;2：</strong></p>

<pre><strong>输入:</strong> -1-&gt;5-&gt;3-&gt;4-&gt;0
<strong>输出:</strong> -1-&gt;0-&gt;3-&gt;4-&gt;5
</pre>



-----

题目标签：Sort / Linked List

题目链接：[LeetCode](https://leetcode.com/problems/insertion-sort-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/insertion-sort-list/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 32  ms | 1.3 MB |

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
    ListNode* insertionSortList(ListNode* head) {
        if (!head) return head;
        ListNode* g = new ListNode(INT_MIN);
        g->next = head;
        ListNode* p = head;
        ListNode* q = nullptr;
        ListNode* t = nullptr;
        while (p && p->next) {
            q = p->next;
            if (p->val > q->val) {
                t = g;
                while (t->next->val <= q->val) {
                    t = t->next;
                }
                p->next = q->next;
                q->next = t->next;
                t->next = q;
            } else {
                p = p->next;
            }
        }
        return g->next;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
