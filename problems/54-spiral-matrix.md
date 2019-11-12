## 54. Spiral Matrix - 螺旋矩阵

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个包含&nbsp;<em>m</em> x <em>n</em>&nbsp;个元素的矩阵（<em>m</em> 行, <em>n</em> 列），请按照顺时针螺旋顺序，返回矩阵中的所有元素。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong>
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
<strong>输出:</strong> [1,2,3,6,9,8,7,4,5]
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong>
[
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9,10,11,12]
]
<strong>输出:</strong> [1,2,3,4,8,12,11,10,9,5,6,7]
</pre>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/spiral-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/spiral-matrix/description/)

## 题解

数组相关的问题要注意下标越界问题。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 44  ms | N/A |

```python3
class Solution:
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        if not matrix or not matrix[0]:
            return []
        res = []
        rows = matrix
        cols = list(zip(*matrix))
        m, n = len(rows), len(cols)
        i = 0
        while True:
            i += 1
            if 0 <= i-1 < m:
                res.extend(rows[i-1][i-1:n-i+1])
                if len(res) == m * n:
                    break
            if 0 <= n-i < n:
                res.extend(cols[n-i][i:m-i+1])
                if len(res) == m * n:
                    break
            if 0 <= m-i < m:
                res.extend(rows[m-i][i-1:n-i][::-1])
                if len(res) == m * n:
                    break
            if 0 <= i-1 < n:
                res.extend(cols[i-1][i:m-i][::-1])
                if len(res) == m * n:
                    break
        return res
```
