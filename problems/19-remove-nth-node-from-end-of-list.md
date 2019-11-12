## 19. Remove Nth Node From End of List - 删除链表的倒数第N个节点

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个链表，删除链表的倒数第&nbsp;<em>n&nbsp;</em>个节点，并且返回链表的头结点。</p>

<p><strong>示例：</strong></p>

<pre>给定一个链表: <strong>1-&gt;2-&gt;3-&gt;4-&gt;5</strong>, 和 <strong><em>n</em> = 2</strong>.

当删除了倒数第二个节点后，链表变为 <strong>1-&gt;2-&gt;3-&gt;5</strong>.
</pre>

<p><strong>说明：</strong></p>

<p>给定的 <em>n</em>&nbsp;保证是有效的。</p>

<p><strong>进阶：</strong></p>

<p>你能尝试使用一趟扫描实现吗？</p>



-----

题目标签：Linked List / Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/description/)

## 题解

比较简单的单链表的题目。由于没有指向前驱的指针，为了定位倒数第n个节点，可以把节点存起来。删除节点时，注意判断待删节点是否是头结点，和待删节点不是头节点时的处理流程有所不同。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | N/A |

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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        vector<ListNode*> st;
        ListNode* hd = head;
        while(hd){
            st.push_back(hd);
            hd = hd->next;
        }
        ListNode* del = st.at(st.size() - n);
        if(del == head){
            ListNode* res = del->next;
            del->next = NULL;
            delete del;
            return res;
        }else{
            ListNode* pre = st.at(st.size() - n - 1);
            pre->next = del->next;
            del->next = NULL;
            delete del;
            return head;
        }
    }
};
```
