## 1171. Remove Zero Sum Consecutive Nodes from Linked List - 从链表中删去总和值为零的连续节点

<!--If you want to use the English description, use `question.content` instead-->

<p>给你一个链表的头节点&nbsp;<code>head</code>，请你编写代码，反复删去链表中由 <strong>总和</strong>&nbsp;值为 <code>0</code> 的连续节点组成的序列，直到不存在这样的序列为止。</p>

<p>删除完毕后，请你返回最终结果链表的头节点。</p>

<p>&nbsp;</p>

<p>你可以返回任何满足题目要求的答案。</p>

<p>（注意，下面示例中的所有序列，都是对&nbsp;<code>ListNode</code>&nbsp;对象序列化的表示。）</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>head = [1,2,-3,3,1]
<strong>输出：</strong>[3,1]
<strong>提示：</strong>答案 [1,2,1] 也是正确的。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>head = [1,2,3,-3,4]
<strong>输出：</strong>[1,2,4]
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>head = [1,2,3,-3,-2]
<strong>输出：</strong>[1]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>给你的链表中可能有 <code>1</code> 到&nbsp;<code>1000</code>&nbsp;个节点。</li>
	<li>对于链表中的每个节点，节点的值：<code>-1000 &lt;= node.val &lt;= 1000</code>.</li>
</ul>



-----

题目标签：Linked List

题目链接：[LeetCode](https://leetcode.com/problems/remove-zero-sum-consecutive-nodes-from-linked-list/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-zero-sum-consecutive-nodes-from-linked-list/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 8  ms | 37.8 MB |

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
    private List<Integer> removeReplic(List<Integer> arr) {
        // for (int i : arr) System.out.print(i + " "); System.out.println("");
        int[] sum = new int[arr.size() + 1];
        for (int i = 0; i < arr.size(); i++) {
            sum[i + 1] = sum[i] + arr.get(i);
        }
        // for (int i : sum) System.out.print(i + " "); System.out.println("");
        int sp = -1;
        HashMap<Integer, Integer> map = new HashMap<>();
        List<Integer> rec = new ArrayList<>();
        for (int i = 0; i < sum.length; i++) {
            if (map.containsKey(sum[i]) && map.get(sum[i]) > sp) {
                rec.add(map.get(sum[i]));
                rec.add(i);
                sp = i;
            } else {
                map.put(sum[i], i);
            }
        }
        // for (int i : rec) System.out.print(i + " "); System.out.println("");
        if (!rec.isEmpty()) {
            List<Integer> rem = new ArrayList<>();
            int t1 = 0;
            int t2 = 1;
            for (int i = 0; i < arr.size(); i++) {
                if (t1 < rec.size() && t2 < rec.size() && i >= rec.get(t1) && i < rec.get(t2)) {
                    continue;
                }
                rem.add(arr.get(i));
                if (t2 < rec.size() && i == rec.get(t2)) {
                    t1 += 2;
                    t2 += 2;
                }
            }
            return removeReplic(rem);
        } else {
            return arr;
        }
    }

    public ListNode removeZeroSumSublists(ListNode head) {
        List<Integer> arr = new ArrayList<>();
        ListNode p = head;
        while (p != null) {
            arr.add(p.val);
            p = p.next;
        }
        List<Integer> rem = removeReplic(arr);
        ListNode dummy = new ListNode(0);
        ListNode tmp = dummy;
        for (int i = 0; i < rem.size(); i++) {
            tmp.next = new ListNode(rem.get(i));
            tmp = tmp.next;
        }
        return dummy.next;
    }
}
```
