## 29. Divide Two Integers - 两数相除

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个整数，被除数&nbsp;<code>dividend</code>&nbsp;和除数&nbsp;<code>divisor</code>。将两数相除，要求不使用乘法、除法和 mod 运算符。</p>

<p>返回被除数&nbsp;<code>dividend</code>&nbsp;除以除数&nbsp;<code>divisor</code>&nbsp;得到的商。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> dividend = 10, divisor = 3
<strong>输出:</strong> 3</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> dividend = 7, divisor = -3
<strong>输出:</strong> -2</pre>

<p><strong>说明:</strong></p>

<ul>
	<li>被除数和除数均为 32 位有符号整数。</li>
	<li>除数不为&nbsp;0。</li>
	<li>假设我们的环境只能存储 32 位有符号整数，其数值范围是 [&minus;2<sup>31</sup>,&nbsp; 2<sup>31&nbsp;</sup>&minus; 1]。本题中，如果除法结果溢出，则返回 2<sup>31&nbsp;</sup>&minus; 1。</li>
</ul>



-----

题目标签：Math / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/divide-two-integers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/divide-two-integers/description/)

## 题解

这题到底想考查什么呢？位运算？

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 52  ms | N/A |

```python3
class Solution:
    def divide(self, dividend, divisor):
        """
        :type dividend: int
        :type divisor: int
        :rtype: int
        """
        rst = abs(dividend) // abs(divisor)
        if (dividend > 0 and divisor < 0) or (dividend < 0 and divisor > 0):
            rst *= -1
        return min(2**31-1, max(-2**31, rst ))
```
