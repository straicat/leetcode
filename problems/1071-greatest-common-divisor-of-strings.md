## 1071. Greatest Common Divisor of Strings - 字符串的最大公因子

<!--If you want to use the English description, use `question.content` instead-->

<p>对于字符串&nbsp;<code>S</code> 和&nbsp;<code>T</code>，只有在 <code>S = T + ... + T</code>（<code>T</code>&nbsp;与自身连接 1 次或多次）时，我们才认定&nbsp;&ldquo;<code>T</code> 能除尽 <code>S</code>&rdquo;。</p>

<p>返回字符串&nbsp;<code>X</code>，要求满足&nbsp;<code>X</code> 能除尽 <code>str1</code> 且&nbsp;<code>X</code> 能除尽 <code>str2</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>str1 = &quot;ABCABC&quot;, str2 = &quot;ABC&quot;
<strong>输出：</strong>&quot;ABC&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>str1 = &quot;ABABAB&quot;, str2 = &quot;ABAB&quot;
<strong>输出：</strong>&quot;AB&quot;
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>str1 = &quot;LEET&quot;, str2 = &quot;CODE&quot;
<strong>输出：</strong>&quot;&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= str1.length &lt;= 1000</code></li>
	<li><code>1 &lt;= str2.length &lt;= 1000</code></li>
	<li><code>str1[i]</code> 和&nbsp;<code>str2[i]</code> 为大写英文字母</li>
</ol>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/greatest-common-divisor-of-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/greatest-common-divisor-of-strings/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | 13.9 MB |

```python3
class Solution:
    def gcdOfStrings(self, str1: str, str2: str) -> str:
        if len(str1) == len(str2):
            return str1 if str1 == str2 else ""
        long, short = (str1, str2) if len(str1) > len(str2) else (str2, str1)
        if long.startswith(short):
            return self.gcdOfStrings(short, long[len(short):])
        else:
            return ""
```
