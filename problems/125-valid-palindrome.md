## 125. Valid Palindrome - 验证回文串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。</p>

<p><strong>说明：</strong>本题中，我们将空字符串定义为有效的回文串。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> &quot;A man, a plan, a canal: Panama&quot;
<strong>输出:</strong> true
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> &quot;race a car&quot;
<strong>输出:</strong> false
</pre>



-----

题目标签：Two Pointers / String

题目链接：[LeetCode](https://leetcode.com/problems/valid-palindrome/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/valid-palindrome/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 52  ms | N/A |

```python3
import re

class Solution:
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        ss = ''.join(re.findall('[a-zA-Z0-9]+', s)).lower()
        return ss == ss[::-1]
```
