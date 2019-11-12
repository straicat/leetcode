## 389. Find the Difference - 找不同

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个字符串 <em><strong>s</strong></em> 和 <em><strong>t</strong></em>，它们只包含小写字母。</p>

<p>字符串&nbsp;<strong><em>t</em></strong>&nbsp;由字符串&nbsp;<strong><em>s</em></strong>&nbsp;随机重排，然后在随机位置添加一个字母。</p>

<p>请找出在 <em><strong>t</strong></em> 中被添加的字母。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre>输入：
s = &quot;abcd&quot;
t = &quot;abcde&quot;

输出：
e

解释：
&#39;e&#39; 是那个被添加的字母。
</pre>



-----

题目标签：Bit Manipulation / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/find-the-difference/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-the-difference/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 40  ms | N/A |

```python3
class Solution:
    def findTheDifference(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: str
        """
        res = 0
        for c in s+t:
            res ^= ord(c)
        return chr(res)
```
