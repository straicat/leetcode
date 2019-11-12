## 62. Unique Paths - 不同路径

<!--If you want to use the English description, use `question.content` instead-->

<p>一个机器人位于一个 <em>m x n </em>网格的左上角 （起始点在下图中标记为&ldquo;Start&rdquo; ）。</p>

<p>机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为&ldquo;Finish&rdquo;）。</p>

<p>问总共有多少条不同的路径？</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/robot_maze.png"></p>

<p><small>例如，上图是一个7 x 3 的网格。有多少可能的路径？</small></p>

<p><strong>说明：</strong><em>m</em>&nbsp;和 <em>n </em>的值均不超过 100。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> m = 3, n = 2
<strong>输出:</strong> 3
<strong>解释:</strong>
从左上角开始，总共有 3 条路径可以到达右下角。
1. 向右 -&gt; 向右 -&gt; 向下
2. 向右 -&gt; 向下 -&gt; 向右
3. 向下 -&gt; 向右 -&gt; 向右
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> m = 7, n = 3
<strong>输出:</strong> 28</pre>



-----

题目标签：Array / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/unique-paths/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/unique-paths/description/)

## 题解

只求有多少种走法，而不是枚举所有走法，所以考虑动态规划。

根据格子建立dp数组。显然，假设起点位于最后一行或最后一列，走法都只有1种。其余位置，走法就是下方一格与右方一格的走法之和。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | N/A |

```python3
class Solution:
    def uniquePaths(self, m, n):
        """
        :type m: int
        :type n: int
        :rtype: int
        """
        dp = [[0] * m for _ in range(n)]
        for i in range(m):
            dp[-1][i] = 1
        for i in range(n):
            dp[i][-1] = 1
        for i in range(n-2, -1, -1):
            for j in range(m-2, -1, -1):
                dp[i][j] = dp[i+1][j] + dp[i][j+1]
        return dp[0][0]
```
