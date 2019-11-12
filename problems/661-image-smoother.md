## 661. Image Smoother - 图片平滑器

<!--If you want to use the English description, use `question.content` instead-->

<p>包含整数的二维矩阵 M 表示一个图片的灰度。你需要设计一个平滑器来让每一个单元的灰度成为平均灰度&nbsp;(向下舍入) ，平均灰度的计算是周围的8个单元和它本身的值求平均，如果周围的单元格不足八个，则尽可能多的利用它们。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong>
[[1,1,1],
 [1,0,1],
 [1,1,1]]
<strong>输出:</strong>
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]
<strong>解释:</strong>
对于点 (0,0), (0,2), (2,0), (2,2): 平均(3/4) = 平均(0.75) = 0
对于点 (0,1), (1,0), (1,2), (2,1): 平均(5/6) = 平均(0.83333333) = 0
对于点 (1,1): 平均(8/9) = 平均(0.88888889) = 0
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>给定矩阵中的整数范围为 [0, 255]。</li>
	<li>矩阵的长和宽的范围均为&nbsp;[1, 150]。</li>
</ol>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/image-smoother/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/image-smoother/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 980  ms | N/A |

```python3
class Solution:
    def imageSmoother(self, M):
        """
        :type M: List[List[int]]
        :rtype: List[List[int]]
        """
        res = [[None] * len(M[0]) for _ in range(len(M))]
        for i in range(len(M)):
            for j in range(len(M[0])):
                tmp = []
                for x in (-1, 0, 1):
                    for y in (-1, 0, 1):
                        if 0 <= i + x < len(M) and 0 <= j + y < len(M[0]):
                            tmp.append(M[i+x][j+y])
                res[i][j] = sum(tmp) // len(tmp)
        return res
```
