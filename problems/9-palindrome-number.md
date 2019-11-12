## 9. Palindrome Number - 回文数

<!--If you want to use the English description, use `question.content` instead-->

<p>判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 121
<strong>输出:</strong> true
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> -121
<strong>输出:</strong> false
<strong>解释:</strong> 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> 10
<strong>输出:</strong> false
<strong>解释:</strong> 从右向左读, 为 01 。因此它不是一个回文数。
</pre>

<p><strong>进阶:</strong></p>

<p>你能不将整数转为字符串来解决这个问题吗？</p>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/palindrome-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/palindrome-number/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 296  ms | N/A |

```python3
class Solution:
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if x < 0:
            return False
        tmp = []
        while x > 9:
            tmp.append(x % 10)
            x //= 10
        tmp.append(x)
        return tmp == tmp[::-1]
```
