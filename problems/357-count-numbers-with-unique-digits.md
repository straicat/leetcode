## 357. Count Numbers with Unique Digits - 计算各个位数不同的数字个数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个<strong>非负</strong>整数 n，计算各位数字都不同的数字 x 的个数，其中 0 &le; x &lt; 10<sup>n&nbsp;</sup>。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入: </strong>2
<strong>输出: </strong>91 
<strong>解释: </strong>答案应为除去 <code>11,22,33,44,55,66,77,88,99 </code>外，在 [0,100) 区间内的所有数字。
</pre>



-----

题目标签：Math / Dynamic Programming / Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/count-numbers-with-unique-digits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/count-numbers-with-unique-digits/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 32  ms | N/A |

```python3
class Solution:
    def countNumbersWithUniqueDigits(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n == 0:
            return 1
        else:
            n = min(n, 10)
            arr = [9, 9, 8, 7, 6, 5, 4, 3, 2, 1]
            a = self.countNumbersWithUniqueDigits(n-1)
            b = 1
            for i in range(n):
                b *= arr[i]
            return a + b
```
