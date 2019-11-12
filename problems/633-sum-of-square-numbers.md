## 633. Sum of Square Numbers - 平方数之和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非负整数&nbsp;<code>c</code>&nbsp;，你要判断是否存在两个整数 <code>a</code> 和 <code>b</code>，使得&nbsp;a<sup>2</sup> + b<sup>2</sup> = c。</p>

<p><strong>示例1:</strong></p>

<pre>
<strong>输入:</strong> 5
<strong>输出:</strong> True
<strong>解释:</strong> 1 * 1 + 2 * 2 = 5
</pre>

<p>&nbsp;</p>

<p><strong>示例2:</strong></p>

<pre>
<strong>输入:</strong> 3
<strong>输出:</strong> False
</pre>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/sum-of-square-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-square-numbers/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 212  ms | N/A |

```python3
class Solution:
    def judgeSquareSum(self, c):
        """
        :type c: int
        :rtype: bool
        """
        tmp = set()
        for i in range(int(c**0.5)+1):
            tmp.add(i*i)
        for ii in tmp:
            if c - ii in tmp:
                return True
        return False
```
