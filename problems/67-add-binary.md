## 67. Add Binary - 二进制求和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个二进制字符串，返回他们的和（用二进制表示）。</p>

<p>输入为<strong>非空</strong>字符串且只包含数字&nbsp;<code>1</code>&nbsp;和&nbsp;<code>0</code>。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> a = &quot;11&quot;, b = &quot;1&quot;
<strong>输出:</strong> &quot;100&quot;</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> a = &quot;1010&quot;, b = &quot;1011&quot;
<strong>输出:</strong> &quot;10101&quot;</pre>



-----

题目标签：Math / String

题目链接：[LeetCode](https://leetcode.com/problems/add-binary/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-binary/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 92  ms | N/A |

```python3
class Solution:
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        return bin(int(a, 2) + int(b, 2))[2:]
```
