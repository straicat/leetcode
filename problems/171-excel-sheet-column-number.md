## 171. Excel Sheet Column Number - Excel表列序号

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个Excel表格中的列名称，返回其相应的列序号。</p>

<p>例如，</p>

<pre>    A -&gt; 1
    B -&gt; 2
    C -&gt; 3
    ...
    Z -&gt; 26
    AA -&gt; 27
    AB -&gt; 28 
    ...
</pre>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> &quot;A&quot;
<strong>输出:</strong> 1
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入: </strong>&quot;AB&quot;
<strong>输出:</strong> 28
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入: </strong>&quot;ZY&quot;
<strong>输出:</strong> 701</pre>

<p><strong>致谢：</strong><br>
特别感谢&nbsp;<a href="http://leetcode.com/discuss/user/ts">@ts</a>&nbsp;添加此问题并创建所有测试用例。</p>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/excel-sheet-column-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/excel-sheet-column-number/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 60  ms | N/A |

```python3
class Solution:
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        res = 0
        for c in s:
            res = 26 * res + ord(c) - ord('A') + 1
        return res
```
