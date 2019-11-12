## 693. Binary Number with Alternating Bits - 交替位二进制数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个正整数，检查他是否为交替位二进制数：换句话说，就是他的二进制数相邻的两个位数永不相等。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> 5
<strong>输出:</strong> True
<strong>解释:</strong>
5的二进制数是: 101
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> 7
<strong>输出:</strong> False
<strong>解释:</strong>
7的二进制数是: 111
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre>
<strong>输入:</strong> 11
<strong>输出:</strong> False
<strong>解释:</strong>
11的二进制数是: 1011
</pre>

<p><strong>&nbsp;示例 4:</strong></p>

<pre>
<strong>输入:</strong> 10
<strong>输出:</strong> True
<strong>解释:</strong>
10的二进制数是: 1010
</pre>



-----

题目标签：Bit Manipulation

题目链接：[LeetCode](https://leetcode.com/problems/binary-number-with-alternating-bits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-number-with-alternating-bits/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | 13.8 MB |

```python3
class Solution:
    def hasAlternatingBits(self, n: int) -> bool:
        b = bin(n)[2:]
        return '00' not in b and '11' not in b
```
