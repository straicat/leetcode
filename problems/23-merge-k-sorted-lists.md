## 23. Merge k Sorted Lists - 合并K个排序链表

<!--If you want to use the English description, use `question.content` instead-->

<p>合并&nbsp;<em>k&nbsp;</em>个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>
[
&nbsp; 1-&gt;4-&gt;5,
&nbsp; 1-&gt;3-&gt;4,
&nbsp; 2-&gt;6
]
<strong>输出:</strong> 1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4-&gt;5-&gt;6</pre>



-----

题目标签：Heap / Linked List / Divide and Conquer

题目链接：[LeetCode](https://leetcode.com/problems/merge-k-sorted-lists/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/merge-k-sorted-lists/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 24  ms | 2.5 MB |

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
static auto x = [](){
    ios::sync_with_stdio(false);
    cin.tie(NULL);
    return 0;
}();
class Solution {
public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        auto cmp = [](int x, int y) { return x > y; };
        priority_queue<int, vector<int>, decltype(cmp)> pq(cmp);
        for (auto t : lists) {
            while (t) {
                pq.push(t->val);
                t = t->next;
            }
        }
        ListNode* p = new ListNode(-1);
        ListNode* res = p;
        while (!pq.empty()) {
            p->next = new ListNode(pq.top());
            pq.pop();
            p = p->next;
        }
        return res->next;
    }
};
```
