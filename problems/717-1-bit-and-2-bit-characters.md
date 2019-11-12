## 717. 1-bit and 2-bit Characters - 1比特与2比特字符

<!--If you want to use the English description, use `question.content` instead-->

<p>有两种特殊字符。第一种字符可以用一比特<code>0</code>来表示。第二种字符可以用两比特(<code>10</code>&nbsp;或&nbsp;<code>11</code>)来表示。</p>

<p>现给一个由若干比特组成的字符串。问最后一个字符是否必定为一个一比特字符。给定的字符串总是由0结束。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>
<strong>输入:</strong> 
bits = [1, 0, 0]
<strong>输出:</strong> True
<strong>解释:</strong> 
唯一的编码方式是一个两比特字符和一个一比特字符。所以最后一个字符是一比特字符。
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre>
<strong>输入:</strong> 
bits = [1, 1, 1, 0]
<strong>输出:</strong> False
<strong>解释:</strong> 
唯一的编码方式是两比特字符和两比特字符。所以最后一个字符不是一比特字符。
</pre>

<p><strong>注意:</strong></p>

<ul>
	<li><code>1 &lt;= len(bits) &lt;= 1000</code>.</li>
	<li><code>bits[i]</code> 总是<code>0</code> 或&nbsp;<code>1</code>.</li>
</ul>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/1-bit-and-2-bit-characters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/1-bit-and-2-bit-characters/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 40  ms | N/A |

```python3
class Solution:
    def isOneBitCharacter(self, bits):
        """
        :type bits: List[int]
        :rtype: bool
        """
        i = 0
        while i < len(bits):
            if i == len(bits) - 1 and bits[i] == 0:
                return True
            if bits[i] == 1:
                i += 2
            else:
                i += 1
        return False
```
