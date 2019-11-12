## 647. Palindromic Substrings - 回文子串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串，你的任务是计算这个字符串中有多少个回文子串。</p>

<p>具有不同开始位置或结束位置的子串，即使是由相同的字符组成，也会被计为是不同的子串。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> &quot;abc&quot;
<strong>输出:</strong> 3
<strong>解释:</strong> 三个回文子串: &quot;a&quot;, &quot;b&quot;, &quot;c&quot;.
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> &quot;aaa&quot;
<strong>输出:</strong> 6
<strong>说明:</strong> 6个回文子串: &quot;a&quot;, &quot;a&quot;, &quot;a&quot;, &quot;aa&quot;, &quot;aa&quot;, &quot;aaa&quot;.
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>输入的字符串长度不会超过1000。</li>
</ol>



-----

题目标签：String / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/palindromic-substrings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/palindromic-substrings/description/)

## 题解

这道题的运行时间居然达到了2060ms，看来方法还是比较暴力，需要考虑更优的做法。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 2060  ms | N/A |

```python3
class Solution:
    def countSubstrings(self, s):
        """
        :type s: str
        :rtype: int
        """
        dp = [0, 1]
        if len(s) < 2:
            return dp[len(s)]
        else:
            for i in range(2, len(s)+1):
                dp.append(dp[i-1] + [s[:i][j:] == s[:i][j:][::-1] for j in range(i)].count(True))
            return dp[-1]
```
