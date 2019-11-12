## 64. Minimum Path Sum - 最小路径和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个包含非负整数的 <em>m</em>&nbsp;x&nbsp;<em>n</em>&nbsp;网格，请找出一条从左上角到右下角的路径，使得路径上的数字总和为最小。</p>

<p><strong>说明：</strong>每次只能向下或者向右移动一步。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>
[
&nbsp; [1,3,1],
  [1,5,1],
  [4,2,1]
]
<strong>输出:</strong> 7
<strong>解释:</strong> 因为路径 1&rarr;3&rarr;1&rarr;1&rarr;1 的总和最小。
</pre>



-----

题目标签：Array / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/minimum-path-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-path-sum/description/)

## 题解

动态规划。

F[i, j] = grid[i, j] + min(F[i+1, j], F[i, j+1])

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 116  ms | N/A |

```python3
class Solution:
    def minPathSum(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        m = len(grid)
        if not m:
            return 0
        n = len(grid[0])
        if not n:
            return 0
        dp = [[0] * n for _ in range(m)]
        for i in range(m-1, -1, -1):
            for j in range(n-1, -1, -1):
                dp[i][j] = grid[i][j]
                if i < m-1 and j < n-1:
                    dp[i][j] += min(dp[i+1][j], dp[i][j+1])
                else:
                    if i < m-1:
                        dp[i][j] += dp[i+1][j]
                    if j < n-1:
                        dp[i][j] += dp[i][j+1]
        return dp[0][0]
```
