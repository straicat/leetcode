## 498. Diagonal Traverse - 对角线遍历

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个含有 M x N 个元素的矩阵（M 行，N 列），请以对角线遍历的顺序返回这个矩阵中的所有元素，对角线遍历如下图所示。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]

<strong>输出:</strong>  [1,2,4,7,5,3,6,8,9]

<strong>解释:</strong>
<img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/diagonal_traverse.png" style="width: 220px;">
</pre>

<p>&nbsp;</p>

<p><strong>说明:</strong></p>

<ol>
	<li>给定矩阵中的元素总数不会超过 100000 。</li>
</ol>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/diagonal-traverse/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/diagonal-traverse/description/)

## 题解

不难，把遍历的过程模拟一下就行，主要是边界情况的处理。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 132  ms | N/A |

```python3
class Solution:
    def findDiagonalOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        if not matrix or not matrix[0]:
            return []
        upright = True
        res = []
        i, j = 0, 0
        while len(res) < len(matrix) * len(matrix[0]):
            res.append(matrix[i][j])
            if upright:
                if i > 0 and j < len(matrix[0])-1:
                    i -= 1
                    j += 1
                else:
                    upright = False
                    if j == len(matrix[0])-1:
                        i += 1
                    else:
                        j += 1
            else:
                if j > 0 and i < len(matrix)-1:
                    i += 1
                    j -= 1
                else:
                    upright = True
                    if i == len(matrix)-1:
                        j += 1
                    else:
                        i += 1
        return res
```
