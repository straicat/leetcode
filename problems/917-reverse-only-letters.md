## 917. Reverse Only Letters - 仅仅反转字母

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串&nbsp;<code>S</code>，返回&nbsp;&ldquo;反转后的&rdquo;&nbsp;字符串，其中不是字母的字符都保留在原地，而所有字母的位置发生反转。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>&quot;ab-cd&quot;
<strong>输出：</strong>&quot;dc-ba&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>&quot;a-bC-dEf-ghIj&quot;
<strong>输出：</strong>&quot;j-Ih-gfE-dCba&quot;
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>&quot;Test1ng-Leet=code-Q!&quot;
<strong>输出：</strong>&quot;Qedo1ct-eeLg=ntse-T!&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>S.length &lt;= 100</code></li>
	<li><code>33 &lt;= S[i].ASCIIcode &lt;= 122</code>&nbsp;</li>
	<li><code>S</code> 中不包含&nbsp;<code>\</code> or <code>&quot;</code></li>
</ol>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/reverse-only-letters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-only-letters/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | N/A |

```python3
class Solution:
    def reverseOnlyLetters(self, S):
        """
        :type S: str
        :rtype: str
        """
        t = list(S)
        i, j = 0, len(t) - 1
        while i < j:
            while i < j and not t[i].isalpha():
                i += 1
            while i < j and not t[j].isalpha():
                j -= 1
            t[i], t[j] = t[j], t[i]
            i += 1
            j -= 1
        return ''.join(t)
```
