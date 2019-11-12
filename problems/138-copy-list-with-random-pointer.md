## 138. Copy List with Random Pointer - 复制带随机指针的链表

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个链表，每个节点包含一个额外增加的随机指针，该指针可以指向链表中的任何节点或空节点。</p>

<p>要求返回这个链表的<strong><a href="https://baike.baidu.com/item/深拷贝/22785317?fr=aladdin" target="_blank">深拷贝</a></strong>。&nbsp;</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/23/1470150906153-2yxeznm.png"></strong></p>

<pre><strong>输入：
</strong>{&quot;$id&quot;:&quot;1&quot;,&quot;next&quot;:{&quot;$id&quot;:&quot;2&quot;,&quot;next&quot;:null,&quot;random&quot;:{&quot;$ref&quot;:&quot;2&quot;},&quot;val&quot;:2},&quot;random&quot;:{&quot;$ref&quot;:&quot;2&quot;},&quot;val&quot;:1}

<strong>解释：
</strong>节点 1 的值是 1，它的下一个指针和随机指针都指向节点 2 。
节点 2 的值是 2，它的下一个指针指向 null，随机指针指向它自己。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>你必须返回<strong>给定头的拷贝</strong>作为对克隆列表的引用。</li>
</ol>



-----

题目标签：Hash Table / Linked List

题目链接：[LeetCode](https://leetcode.com/problems/copy-list-with-random-pointer/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/copy-list-with-random-pointer/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 48  ms | 3.6 MB |

```cpp
/**
 * Definition for singly-linked list with a random pointer.
 * struct RandomListNode {
 *     int label;
 *     RandomListNode *next, *random;
 *     RandomListNode(int x) : label(x), next(NULL), random(NULL) {}
 * };
 */
class Solution {
public:
    unordered_map<RandomListNode*, RandomListNode*> M;
    RandomListNode *copyRandomList(RandomListNode *head) {
        if (!head) return NULL;
        if (M.count(head)) return M[head];
        RandomListNode* tmp = new RandomListNode(head->label);
        M.insert({head, tmp});
        if (head->next) tmp->next = copyRandomList(head->next);
        if (head->random) tmp->random = copyRandomList(head->random);
        return tmp;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
