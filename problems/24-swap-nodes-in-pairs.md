## 24. Swap Nodes in Pairs - 两两交换链表中的节点

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。</p>

<p><strong>你不能只是单纯的改变节点内部的值</strong>，而是需要实际的进行节点交换。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre>给定 <code>1-&gt;2-&gt;3-&gt;4</code>, 你应该返回 <code>2-&gt;1-&gt;4-&gt;3</code>.
</pre>



-----

题目标签：Linked List

题目链接：[LeetCode](https://leetcode.com/problems/swap-nodes-in-pairs/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/swap-nodes-in-pairs/description/)

## 题解

单链表指针操作。注意空指针判断。

另外，交换相邻两个节点时，如果不是在头部，那么，这两个节点前面的那个节点的next指针也要做修改！

交换头部两个节点时，头结点在交换后变成了原先的第二个节点，因此要把第二个节点暂存起来以便返回结果。

头部两个节点交换时要单独处理。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | N/A |

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
    void swap(ListNode* a){
        // a->b->c->d
        // a->c->b->d
        if(a && a->next && a->next->next){
            ListNode* b = a->next;
            ListNode* c = b->next;
            b->next = c->next;
            c->next = b;
            a->next = c;
        }
    }
    ListNode* swapPairs(ListNode* head) {
        if(head && head->next){
            ListNode* res = head->next;
            head->next = res->next;
            res->next = head;
            while(head && head->next && head->next->next){
                swap(head);
                head = head->next->next;
            }
            return res;
        }else{
            return head;
        }
    }
};
```
