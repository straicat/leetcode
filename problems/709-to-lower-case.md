## 709. To Lower Case - 转换成小写字母

<!--If you want to use the English description, use `question.content` instead-->

<p>实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入: </strong>&quot;Hello&quot;
<strong>输出: </strong>&quot;hello&quot;</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入: </strong>&quot;here&quot;
<strong>输出: </strong>&quot;here&quot;</pre>

<p><strong>示例</strong><strong>&nbsp;3：</strong></p>

<pre>
<strong>输入: </strong>&quot;LOVELY&quot;
<strong>输出: </strong>&quot;lovely&quot;
</pre>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/to-lower-case/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/to-lower-case/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 40  ms | N/A |

```python3
class Solution:
    def toLowerCase(self, str):
        """
        :type str: str
        :rtype: str
        """
        return str.lower()
```
