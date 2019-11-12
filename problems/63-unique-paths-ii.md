## 63. Unique Paths II - 不同路径 II

<!--If you want to use the English description, use `question.content` instead-->

<p>一个机器人位于一个 <em>m x n </em>网格的左上角 （起始点在下图中标记为&ldquo;Start&rdquo; ）。</p>

<p>机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为&ldquo;Finish&rdquo;）。</p>

<p>现在考虑网格中有障碍物。那么从左上角到右下角将会有多少条不同的路径？</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/robot_maze.png" style="height: 183px; width: 400px;"></p>

<p>网格中的障碍物和空位置分别用 <code>1</code> 和 <code>0</code> 来表示。</p>

<p><strong>说明：</strong><em>m</em>&nbsp;和 <em>n </em>的值均不超过 100。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:
</strong>[
&nbsp; [0,0,0],
&nbsp; [0,1,0],
&nbsp; [0,0,0]
]
<strong>输出:</strong> 2
<strong>解释:</strong>
3x3 网格的正中间有一个障碍物。
从左上角到右下角一共有 <code>2</code> 条不同的路径：
1. 向右 -&gt; 向右 -&gt; 向下 -&gt; 向下
2. 向下 -&gt; 向下 -&gt; 向右 -&gt; 向右
</pre>



-----

题目标签：Array / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/unique-paths-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/unique-paths-ii/description/)

## 题解

使用动态规划。如果当前位置有障碍，从当前位置到终点的走法为0；否则就是右方一格与下方一格走法之和。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | N/A |

```python3
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid):
        """
        :type obstacleGrid: List[List[int]]
        :rtype: int
        """
        m = len(obstacleGrid)
        if not m:
            return 0
        n = len(obstacleGrid[0])
        dp = [[0] * n for _ in range(m)]
        dp[-1][-1] = int(obstacleGrid[-1][-1] == 0)
        for i in range(m-2, -1, -1):
            dp[i][-1] = int(obstacleGrid[i][-1] == 0) * dp[i+1][-1]
        for i in range(n-2, -1, -1):
            dp[-1][i] = int(obstacleGrid[-1][i] == 0) * dp[-1][i+1]
        for i in range(m-2, -1, -1):
            for j in range(n-2, -1, -1):
                dp[i][j] = int(obstacleGrid[i][j] == 0) * (dp[i+1][j] + dp[i][j+1])
        return dp[0][0]
```
