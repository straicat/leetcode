## 205. Isomorphic Strings - 同构字符串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个字符串&nbsp;<em><strong>s&nbsp;</strong></em>和&nbsp;<strong><em>t</em></strong>，判断它们是否是同构的。</p>

<p>如果&nbsp;<em><strong>s&nbsp;</strong></em>中的字符可以被替换得到&nbsp;<strong><em>t&nbsp;</em></strong>，那么这两个字符串是同构的。</p>

<p>所有出现的字符都必须用另一个字符替换，同时保留字符的顺序。两个字符不能映射到同一个字符上，但字符可以映射自己本身。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <strong><em>s</em></strong> = <code>&quot;egg&quot;, </code><strong><em>t = </em></strong><code>&quot;add&quot;</code>
<strong>输出:</strong> true
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> <strong><em>s</em></strong> = <code>&quot;foo&quot;, </code><strong><em>t = </em></strong><code>&quot;bar&quot;</code>
<strong>输出:</strong> false</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> <strong><em>s</em></strong> = <code>&quot;paper&quot;, </code><strong><em>t = </em></strong><code>&quot;title&quot;</code>
<strong>输出:</strong> true</pre>

<p><strong>说明:</strong><br>
你可以假设&nbsp;<em><strong>s&nbsp;</strong></em>和 <strong><em>t </em></strong>具有相同的长度。</p>



-----

题目标签：Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/isomorphic-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/isomorphic-strings/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 72  ms | N/A |

```python3
class Solution:
    def isIsomorphic(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        if len(s) != len(t):
            return False
        d = {}
        for a, b in zip(s, t):
            if a in d:
                if d[a] != b:
                    return False
            else:
                if b not in d.values():
                    d[a] = b
                else:
                    return False
        return True
```
