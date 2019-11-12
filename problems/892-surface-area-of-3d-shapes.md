## 892. Surface Area of 3D Shapes - 三维形体的表面积

<!--If you want to use the English description, use `question.content` instead-->

<p>在&nbsp;<code>N&nbsp;*&nbsp;N</code>&nbsp;的网格上，我们放置一些&nbsp;<code>1 * 1 * 1&nbsp;</code>&nbsp;的立方体。</p>

<p>每个值&nbsp;<code>v = grid[i][j]</code>&nbsp;表示&nbsp;<code>v</code>&nbsp;个正方体叠放在对应单元格&nbsp;<code>(i, j)</code>&nbsp;上。</p>

<p>请你返回最终形体的表面积。</p>

<p>&nbsp;</p>

<ul>
</ul>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[[2]]
<strong>输出：</strong>10
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[[1,2],[3,4]]
<strong>输出：</strong>34
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>[[1,0],[0,2]]
<strong>输出：</strong>16
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>[[1,1,1],[1,0,1],[1,1,1]]
<strong>输出：</strong>32
</pre>

<p><strong>示例&nbsp;5：</strong></p>

<pre><strong>输入：</strong>[[2,2,2],[2,1,2],[2,2,2]]
<strong>输出：</strong>46
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= N &lt;= 50</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 50</code></li>
</ul>



-----

题目标签：Geometry / Math

题目链接：[LeetCode](https://leetcode.com/problems/surface-area-of-3d-shapes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/surface-area-of-3d-shapes/description/)

## 题解

题目与[883. Projection Area of 3D Shapes](https://leetcode.com/problems/projection-area-of-3d-shapes/description/)很接近，很容易让人往投影方向想，其实并不是利用投影求表面积，因为投影会漏掉凹处的表面积。思路就是：最前和最后块的高度（如果是同一块，这个要加两次）+中间块的相邻高度差。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 92  ms | N/A |

```python3
class Solution:
    def surfaceArea(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        res = 0
        for g in grid + list(zip(*grid)):
            res += len(g) - g.count(0)
            for i, s in enumerate(g):
                if i == 0 or i == len(g) - 1:
                    res += s * (1 + int(len(g) == 1))
                if i > 0:
                    res += abs(g[i] - g[i-1])
        return res
```
