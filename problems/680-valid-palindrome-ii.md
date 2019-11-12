## 680. Valid Palindrome II - 验证回文字符串 Ⅱ

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非空字符串&nbsp;<code>s</code>，<strong>最多</strong>删除一个字符。判断是否能成为回文字符串。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> &quot;aba&quot;
<strong>输出:</strong> True
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> &quot;abca&quot;
<strong>输出:</strong> True
<strong>解释:</strong> 你可以删除c字符。
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>字符串只包含从 a-z 的小写字母。字符串的最大长度是50000。</li>
</ol>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/valid-palindrome-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/valid-palindrome-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 216  ms | N/A |

```python3
class Solution:
    def validPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        if s == s[::-1]:
            return True
        else:
            for i in range(len(s)):
                j = len(s) - 1 - i
                if i < j:
                    if s[i] == s[j]:
                        pass
                    else:
                        for k in (i, j):
                            t = s[:k] + s[k+1:]
                            if t == t[::-1]:
                                return True
                        return False
                else:
                    break
```
