## 521. Longest Uncommon Subsequence I  - 最长特殊序列 Ⅰ

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个字符串，你需要从这两个字符串中找出最长的特殊序列。最长特殊序列定义如下：该序列为某字符串独有的最长子序列（即不能是其他字符串的子序列）。</p>

<p><strong>子序列</strong>可以通过删去字符串中的某些字符实现，但不能改变剩余字符的相对顺序。空序列为所有字符串的子序列，任何字符串为其自身的子序列。</p>

<p>输入为两个字符串，输出最长特殊序列的长度。如果不存在，则返回 -1。</p>

<p><strong>示例 :</strong></p>

<pre><strong>输入:</strong> &quot;aba&quot;, &quot;cdc&quot;
<strong>输出:</strong> 3
<strong>解析:</strong> 最长特殊序列可为 &quot;aba&quot; (或 &quot;cdc&quot;)
</pre>

<p><strong>说明:</strong></p>

<ol>
	<li>两个字符串长度均小于100。</li>
	<li>字符串中的字符仅含有&nbsp;&#39;a&#39;~&#39;z&#39;。</li>
</ol>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/longest-uncommon-subsequence-i/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-uncommon-subsequence-i/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | N/A |

```python3
class Solution:
    def findLUSlength(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: int
        """
        return -1 if a == b else max(len(a), len(b))
```
