## 409. Longest Palindrome - 最长回文串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个包含大写字母和小写字母的字符串，找到通过这些字母构造成的最长的回文串。</p>

<p>在构造过程中，请注意区分大小写。比如&nbsp;<code>&quot;Aa&quot;</code>&nbsp;不能当做一个回文字符串。</p>

<p><strong>注意:</strong><br />
假设字符串的长度不会超过 1010。</p>

<p><strong>示例 1: </strong></p>

<pre>
输入:
&quot;abccccdd&quot;

输出:
7

解释:
我们可以构造的最长的回文串是&quot;dccaccd&quot;, 它的长度是 7。
</pre>



-----

题目标签：Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/longest-palindrome/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-palindrome/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 68  ms | N/A |

```python3
class Solution:
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: int
        """
        res = 0
        for n in collections.Counter(s).values():
            res += n - int(n % 2)
        return res + int(res < len(s))
```
