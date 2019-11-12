## 507. Perfect Number - 完美数

<!--If you want to use the English description, use `question.content` instead-->

<p>对于一个&nbsp;<strong>正整数</strong>，如果它和除了它自身以外的所有正因子之和相等，我们称它为&ldquo;完美数&rdquo;。</p>

<p>给定一个&nbsp;<strong>整数&nbsp;</strong><code>n</code>，&nbsp;如果他是完美数，返回&nbsp;<code>True</code>，否则返回&nbsp;<code>False</code></p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入:</strong> 28
<strong>输出:</strong> True
<strong>解释:</strong> 28 = 1 + 2 + 4 + 7 + 14
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<p>输入的数字&nbsp;<strong><code>n</code></strong> 不会超过 100,000,000. (1e8)</p>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/perfect-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/perfect-number/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 52  ms | N/A |

```python3
class Solution:
    def checkPerfectNumber(self, num):
        """
        :type num: int
        :rtype: bool
        """
        if num < 2:
            return False
        ds = {1}
        for i in range(2, int(num ** 0.5)+1):
            if num % i == 0:
                ds.add(i)
                ds.add(num // i)
        return num == sum(ds)
```
