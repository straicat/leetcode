## 2. Add Two Numbers - 两数相加

<!--If you want to use the English description, use `question.content` instead-->

<p>给出两个&nbsp;<strong>非空</strong> 的链表用来表示两个非负的整数。其中，它们各自的位数是按照&nbsp;<strong>逆序</strong>&nbsp;的方式存储的，并且它们的每个节点只能存储&nbsp;<strong>一位</strong>&nbsp;数字。</p>

<p>如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。</p>

<p>您可以假设除了数字 0 之外，这两个数都不会以 0&nbsp;开头。</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>(2 -&gt; 4 -&gt; 3) + (5 -&gt; 6 -&gt; 4)
<strong>输出：</strong>7 -&gt; 0 -&gt; 8
<strong>原因：</strong>342 + 465 = 807
</pre>



-----

题目标签：Linked List / Math

题目链接：[LeetCode](https://leetcode.com/problems/add-two-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-two-numbers/description/)

## 题解

实际上就是考查大数相加，以链表的形式。不过，有几点需要注意：

1、空链表判断

2、链表可能长度不一致

3、可能会有进位，进位需要传递到下一节点，节点值=节点和+进位。

4、尾部不要添加多余的节点

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 76  ms | 13.9 MB |

```python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        if l1 is None: return l2
        if l2 is None: return l1

        rem = 0
        ret = dummy = ListNode(-1)
        while l1 or l2 or rem:
            a = 0 if l1 is None else l1.val
            b = 0 if l2 is None else l2.val
            val = a + b + rem
            dummy.next = ListNode(val % 10)
            rem = val // 10
            if l1 is not None: l1 = l1.next
            if l2 is not None: l2 = l2.next
            dummy = dummy.next
        return ret.next
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 20  ms | 48.4 MB |

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(-1);
        ListNode t = dummy;
        int carry = 0;
        while (carry > 0 || l1 != null || l2 != null) {
            int sum = carry + (l1 == null ? 0 : l1.val) + (l2 == null ? 0 : l2.val);
            t.next = new ListNode(sum % 10);
            carry = sum / 10;
            if (l1 != null) l1 = l1.next;
            if (l2 != null) l2 = l2.next;
            t = t.next;
        }
        return dummy.next;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 28  ms | N/A |

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        if(!l1){
            return l2;
        }
        if(!l2){
            return l1;
        }
        ListNode* rst = new ListNode(NULL);
        int n1, n2;
        ListNode* res = rst;
        while(true){
            if(l1){
                n1 = l1->val;
                l1 = l1->next;
            }else{
                n1 = NULL;
            }
            if(l2){
                n2 = l2->val;
                l2 = l2->next;
            }else{
                n2 = NULL;
            }
            rst->val += (int)n1 + (int)n2;
            if(l1 || l2 || rst->val >= 10){
                rst->next = new ListNode(rst->val / 10);
                rst->val %= 10;
                rst = rst->next;
            }else{
                break;
            }
        }
        return res;
    }
};
```
