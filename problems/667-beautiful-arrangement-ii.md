## 667. Beautiful Arrangement II - 优美的排列 II

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个整数&nbsp;<code>n</code>&nbsp;和&nbsp;<code>k</code>，你需要实现一个数组，这个数组包含从&nbsp;<code>1</code>&nbsp;到&nbsp;<code>n</code>&nbsp;的 <code>n</code>&nbsp;个不同整数，同时满足以下条件：</p>

<p>① 如果这个数组是 [a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub>, ... , a<sub>n</sub>] ，那么数组&nbsp;[|a<sub>1</sub> - a<sub>2</sub>|, |a<sub>2</sub> - a<sub>3</sub>|, |a<sub>3</sub> - a<sub>4</sub>|, ... , |a<sub>n-1</sub> - a<sub>n</sub>|] 中应该有且仅有&nbsp;k 个不同整数；.</p>

<p>② 如果存在多种答案，你只需实现并返回其中任意一种.</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> n = 3, k = 1
<strong>输出:</strong> [1, 2, 3]
<strong>解释:</strong> [1, 2, 3] 包含 3 个范围在 1-3 的不同整数， 并且 [1, 1] 中有且仅有 1 个不同整数 : 1
</pre>

<p>&nbsp;</p>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> n = 3, k = 2
<strong>输出:</strong> [1, 3, 2]
<strong>解释:</strong> [1, 3, 2] 包含 3 个范围在 1-3 的不同整数， 并且 [2, 1] 中有且仅有 2 个不同整数: 1 和 2
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ol>
	<li>&nbsp;<code>n</code>&nbsp;和&nbsp;<code>k</code>&nbsp;满足条件&nbsp;1 &lt;= k &lt; n &lt;= 10<sup>4</sup>.</li>
</ol>

<p>&nbsp;</p>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/beautiful-arrangement-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/beautiful-arrangement-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 124  ms | N/A |

```python3
class Solution:
    def constructArray(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: List[int]
        """
        res = [1]
        for i, x in enumerate(range(k, 0, -1)):
            res.append(res[i] + [1, -1][i%2] * x)
        for i in range(2+k, n+1):
            res.append(i)
        return res
```
