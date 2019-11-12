## 1034. Coloring A Border - 边框着色

<!--If you want to use the English description, use `question.content` instead-->

<p>给出一个二维整数网格&nbsp;<code>grid</code>，网格中的每个值表示该位置处的网格块的颜色。</p>

<p>只有当两个网格块的颜色相同，而且在四个方向中任意一个方向上相邻时，它们属于同一<strong>连通分量</strong>。</p>

<p>连通分量的<strong>边界</strong>是指连通分量中的所有与不在分量中的正方形相邻（四个方向上）的所有正方形，或者在网格的边界上（第一行/列或最后一行/列）的所有正方形。</p>

<p>给出位于&nbsp;<code>(r0, c0)</code>&nbsp;的网格块和颜色&nbsp;<code>color</code>，使用指定颜色&nbsp;<code>color</code>&nbsp;为所给网格块的连通分量的边界进行着色，并返回最终的网格&nbsp;<code>grid</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>grid = [[1,1],[1,2]], r0 = 0, c0 = 0, color = 3
<strong>输出：</strong>[[3, 3], [3, 2]]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>grid = [[1,2,2],[2,3,2]], r0 = 0, c0 = 1, color = 3
<strong>输出：</strong>[[1, 3, 3], [2, 3, 3]]
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>grid = [[1,1,1],[1,1,1],[1,1,1]], r0 = 1, c0 = 1, color = 2
<strong>输出：</strong>[[2, 2, 2], [2, 1, 2], [2, 2, 2]]</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= grid.length &lt;= 50</code></li>
	<li><code>1 &lt;= grid[0].length &lt;= 50</code></li>
	<li><code>1 &lt;= grid[i][j] &lt;= 1000</code></li>
	<li><code>0 &lt;= r0 &lt; grid.length</code></li>
	<li><code>0 &lt;= c0 &lt; grid[0].length</code></li>
	<li><code>1 &lt;= color &lt;= 1000</code></li>
</ol>

<p>&nbsp;</p>



-----

题目标签：Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/coloring-a-border/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/coloring-a-border/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 96  ms | 13 MB |

```python3
class Solution:
    dx = [-1, 1, 0, 0]
    dy = [0, 0, 1, -1]
    
    def dfs(self, g, m, v, i, j, c):
        # print(i, j)
        if i < 0 or i > len(g) or j < 0 or j > len(g[0]) or g[i][j] != c:
            return
        # 访问
        v[i][j] = 1
        # 判断是否符合涂色条件
        for di in range(4):
            x = i + __class__.dx[di]
            y = j + __class__.dy[di]
            if 0 <= x < len(g) and 0 <= y < len(g[0]) and g[x][y] == c:
                if not v[x][y]:
                    self.dfs(g, m, v, x, y, c)
            else:
                m[i][j] = 1
        
    def colorBorder(self, grid: List[List[int]], r0: int, c0: int, color: int) -> List[List[int]]:
        if not grid or not grid[0]:
            return grid
        if r0 < 0 or r0 > len(grid) or c0 < 0 or c0 > len(grid[0]):
            return grid
        c = grid[r0][c0]
        m = [ [0] * len(grid[0]) for _ in range(len(grid)) ]
        v = [ [0] * len(grid[0]) for _ in range(len(grid)) ]
        self.dfs(grid, m, v, r0, c0, c)
        for i in range(len(m)):
            for j in range(len(m[0])):
                if m[i][j]:
                    grid[i][j] = color
        return grid
```
