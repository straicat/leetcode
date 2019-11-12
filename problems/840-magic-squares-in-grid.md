## 840. Magic Squares In Grid - 矩阵中的幻方

<!--If you want to use the English description, use `question.content` instead-->

<p>3 x 3 的幻方是一个填充有<strong>从 1 到 9</strong> 的不同数字的 3 x 3 矩阵，其中每行，每列以及两条对角线上的各数之和都相等。</p>

<p>给定一个由整数组成的 <code>grid</code>，其中有多少个 3 &times; 3 的 &ldquo;幻方&rdquo; 子矩阵？（每个子矩阵都是连续的）。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入: </strong>[[4,3,8,4],
      [9,5,1,9],
      [2,7,6,2]]
<strong>输出: </strong>1
<strong>解释: </strong>
下面的子矩阵是一个 3 x 3 的幻方：
438
951
276

而这一个不是：
384
519
762

总的来说，在本示例所给定的矩阵中只有一个 3 x 3 的幻方子矩阵。
</pre>

<p><strong>提示:</strong></p>

<ol>
	<li><code>1 &lt;= grid.length&nbsp;&lt;= 10</code></li>
	<li><code>1 &lt;= grid[0].length&nbsp;&lt;= 10</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 15</code></li>
</ol>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/magic-squares-in-grid/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/magic-squares-in-grid/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 44  ms | N/A |

```python3
class Solution:
    def numMagicSquaresInside(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        if len(grid) < 3 or len(grid[0]) < 3:
            return 0
        res = 0
        for i in range(1, len(grid)-1):
            for j in range(1, len(grid[0])-1):
                aa = []
                aaa = []
                for x in (-1, 0, 1):
                    aa.append([])
                    for y in (-1, 0, 1):
                        aa[-1].append(grid[i+x][j+y])
                        aaa.append(grid[i+x][j+y])
                if len(set(filter(lambda a: 1 <= a <= 9, aaa))) == 9:
                    tmp = []
                    tmp.extend([sum(aa[z]) for z in range(3)])
                    tmp.extend([sum(list(zip(*aa))[z]) for z in range(3)])
                    tmp.append(aa[0][0] + aa[1][1] + aa[2][2])
                    tmp.append(aa[0][2] + aa[1][1] + aa[2][0])
                    if len(set(tmp)) == 1:
                        res += 1
        return res
```
