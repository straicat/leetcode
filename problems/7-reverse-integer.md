## 7. Reverse Integer - 整数反转

<!--If you want to use the English description, use `question.content` instead-->

<p>给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> 123
<strong>输出:</strong> 321
</pre>

<p><strong>&nbsp;示例 2:</strong></p>

<pre><strong>输入:</strong> -123
<strong>输出:</strong> -321
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> 120
<strong>输出:</strong> 21
</pre>

<p><strong>注意:</strong></p>

<p>假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为&nbsp;[&minus;2<sup>31</sup>,&nbsp; 2<sup>31&nbsp;</sup>&minus; 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。</p>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/reverse-integer/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-integer/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 64  ms | N/A |

```python3
class Solution:
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        res = int(int(x<0)*'-'+str(x)[int(x<0):][::-1])
        return (-2147483648 <= res <= 2147483647) * res
```
