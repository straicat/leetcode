## 131. Palindrome Partitioning - 分割回文串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串 <em>s</em>，将<em> s </em>分割成一些子串，使每个子串都是回文串。</p>

<p>返回 <em>s</em> 所有可能的分割方案。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>&nbsp;&quot;aab&quot;
<strong>输出:</strong>
[
  [&quot;aa&quot;,&quot;b&quot;],
  [&quot;a&quot;,&quot;a&quot;,&quot;b&quot;]
]</pre>



-----

题目标签：Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/palindrome-partitioning/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/palindrome-partitioning/description/)

## 题解

本题可以使用递归。思路是：如果是空串，就返回`[[]]`；否则，分割`s`，如果分割处左侧是回文串，就把它和右侧的回文子串组合联合起来。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 228  ms | N/A |

```python3
class Solution:
    def partition(self, s):
        """
        :type s: str
        :rtype: List[List[str]]
        """
        if not s:
            return [[]]
        res = []
        for i in range(len(s)):
            if s[:i+1] == s[:i+1][::-1]:
                for ss in self.partition(s[i+1:]):
                    res.append([s[:i+1], *ss])
        return res
```
