## 367. Valid Perfect Square - 有效的完全平方数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个正整数 <em>num</em>，编写一个函数，如果 <em>num</em> 是一个完全平方数，则返回 True，否则返回 False。</p>

<p><strong>说明：</strong>不要使用任何内置的库函数，如&nbsp; <code>sqrt</code>。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>16
<strong>输出：</strong>True</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>14
<strong>输出：</strong>False
</pre>



-----

题目标签：Math / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/valid-perfect-square/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/valid-perfect-square/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 44  ms | N/A |

```python3
class Solution:
    def isPerfectSquare(self, num):
        """
        :type num: int
        :rtype: bool
        """
        if num % 10 in (2, 3, 7, 8):
            return False
        i = 1
        while num > 0:
            num -= i
            if num == 0:
                return True
            i += 2
        return False
```
