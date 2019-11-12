## 695. Max Area of Island - 岛屿的最大面积

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个包含了一些 0 和 1的非空二维数组&nbsp;<code>grid</code>&nbsp;, 一个&nbsp;<strong>岛屿</strong>&nbsp;是由四个方向 (水平或垂直) 的&nbsp;<code>1</code>&nbsp;(代表土地) 构成的组合。你可以假设二维矩阵的四个边缘都被水包围着。</p>

<p>找到给定的二维数组中最大的岛屿面积。(如果没有岛屿，则返回面积为0。)</p>

<p><strong>示例 1:</strong></p>

<pre>
[[0,0,1,0,0,0,0,1,0,0,0,0,0],
 [0,0,0,0,0,0,0,1,1,1,0,0,0],
 [0,1,1,0,1,0,0,0,0,0,0,0,0],
 [0,1,0,0,1,1,0,0,<strong>1</strong>,0,<strong>1</strong>,0,0],
 [0,1,0,0,1,1,0,0,<strong>1</strong>,<strong>1</strong>,<strong>1</strong>,0,0],
 [0,0,0,0,0,0,0,0,0,0,<strong>1</strong>,0,0],
 [0,0,0,0,0,0,0,1,1,1,0,0,0],
 [0,0,0,0,0,0,0,1,1,0,0,0,0]]
</pre>

<p>对于上面这个给定矩阵应返回&nbsp;<code>6</code>。注意答案不应该是11，因为岛屿只能包含水平或垂直的四个方向的&lsquo;1&rsquo;。</p>

<p><strong>示例 2:</strong></p>

<pre>
[[0,0,0,0,0,0,0,0]]</pre>

<p>对于上面这个给定的矩阵, 返回&nbsp;<code>0</code>。</p>

<p><strong>注意:&nbsp;</strong>给定的矩阵<code>grid</code>&nbsp;的长度和宽度都不超过 50。</p>



-----

题目标签：Depth-first Search / Array

题目链接：[LeetCode](https://leetcode.com/problems/max-area-of-island/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/max-area-of-island/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 31  ms | 30.5 MB |

```java
class Solution {
    private int dfs(int[][] g, int x, int y) {
        if (x >= 0 && x < g.length && y >= 0 && y < g[0].length && g[x][y] == 1) {
            g[x][y] = -1;
            return 1 + dfs(g, x - 1, y) + dfs(g, x + 1, y) + dfs(g, x, y - 1) + dfs(g, x, y + 1);
        } else {
            return 0;
        }
    }

    public int maxAreaOfIsland(int[][] grid) {
        int res = 0;
        for (int x = 0; x < grid.length; x++) {
            for (int y = 0; y < grid[0].length; y++) {
                res = Math.max(res, dfs(grid, x, y));
            }
        }
        return res;
    }
}
```
