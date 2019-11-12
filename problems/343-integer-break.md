## 343. Integer Break - 整数拆分

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个正整数&nbsp;<em>n</em>，将其拆分为<strong>至少</strong>两个正整数的和，并使这些整数的乘积最大化。 返回你可以获得的最大乘积。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>2
<strong>输出: </strong>1
<strong>解释: </strong>2 = 1 + 1, 1 &times; 1 = 1。</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入: </strong>10
<strong>输出: </strong>36
<strong>解释: </strong>10 = 3 + 3 + 4, 3 &times;&nbsp;3 &times;&nbsp;4 = 36。</pre>

<p><strong>说明: </strong>你可以假设&nbsp;<em>n&nbsp;</em>不小于 2 且不大于 58。</p>



-----

题目标签：Math / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/integer-break/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/integer-break/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | N/A |

```python3
class Solution:
    def integerBreak(self, n):
        """
        :type n: int
        :rtype: int
        """
        tmp = [0, 0, 1, 2, 4, 6, 9]
        if n < 7:
            return tmp[n]
        else:
            for i in range(7, n+1):
                tmp.append(3*tmp[i-3])
            return tmp[-1]
```
