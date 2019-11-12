## 387. First Unique Character in a String - 字符串中的第一个唯一字符

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。</p>

<p><strong>案例:</strong></p>

<pre>
s = &quot;leetcode&quot;
返回 0.

s = &quot;loveleetcode&quot;,
返回 2.
</pre>

<p>&nbsp;</p>

<p><strong>注意事项：</strong>您可以假定该字符串只包含小写字母。</p>



-----

题目标签：Hash Table / String

题目链接：[LeetCode](https://leetcode.com/problems/first-unique-character-in-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/first-unique-character-in-a-string/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 208  ms | N/A |

```python3
class Solution:
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        d = collections.OrderedDict()
        for c in s:
            d[c] = d.get(c, 0) + 1
        for c, n in d.items():
            if n == 1:
                return s.index(c)
        return -1
```
