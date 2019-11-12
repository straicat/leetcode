## 143. Reorder List - 重排链表

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个单链表&nbsp;<em>L</em>：<em>L</em><sub>0</sub>&rarr;<em>L</em><sub>1</sub>&rarr;&hellip;&rarr;<em>L</em><sub><em>n</em>-1</sub>&rarr;<em>L</em><sub>n ，</sub><br>
将其重新排列后变为： <em>L</em><sub>0</sub>&rarr;<em>L</em><sub><em>n</em></sub>&rarr;<em>L</em><sub>1</sub>&rarr;<em>L</em><sub><em>n</em>-1</sub>&rarr;<em>L</em><sub>2</sub>&rarr;<em>L</em><sub><em>n</em>-2</sub>&rarr;&hellip;</p>

<p>你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>给定链表 1-&gt;2-&gt;3-&gt;4, 重新排列为 1-&gt;4-&gt;2-&gt;3.</pre>

<p><strong>示例 2:</strong></p>

<pre>给定链表 1-&gt;2-&gt;3-&gt;4-&gt;5, 重新排列为 1-&gt;5-&gt;2-&gt;4-&gt;3.</pre>



-----

题目标签：Linked List

题目链接：[LeetCode](https://leetcode.com/problems/reorder-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reorder-list/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 64  ms | 4 MB |

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
    void reorderList(ListNode* head) {
        if (!head) return;
        vector<ListNode* > V;
        ListNode* p = head;
        while (p) {
            V.push_back(p);
            p = p->next;
        }
        int n = V.size();
        for (int i=0; i<n/2; ++i) {
            V[i]->next = V[n-i-1];
        }
        for (int i=n/2; i<n; ++i) {
            V[i]->next = V[n-i];
        }
        V[n/2]->next = NULL;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
