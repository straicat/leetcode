## 931. Minimum Falling Path Sum - 下降路径最小和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个<strong>方形</strong>整数数组&nbsp;<code>A</code>，我们想要得到通过 <code>A</code> 的<em>下降路径</em>的<strong>最小</strong>和。</p>

<p>下降路径可以从第一行中的任何元素开始，并从每一行中选择一个元素。在下一行选择的元素和当前行所选元素最多相隔一列。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[[1,2,3],[4,5,6],[7,8,9]]
<strong>输出：</strong>12
<strong>解释：</strong>
可能的下降路径有：
</pre>

<ul>
	<li><code>[1,4,7], [1,4,8], [1,5,7], [1,5,8], [1,5,9]</code></li>
	<li><code>[2,4,7], [2,4,8], [2,5,7], [2,5,8], [2,5,9], [2,6,8], [2,6,9]</code></li>
	<li><code>[3,5,7], [3,5,8], [3,5,9], [3,6,8], [3,6,9]</code></li>
</ul>

<p>和最小的下降路径是&nbsp;<code>[1,4,7]</code>，所以答案是&nbsp;<code>12</code>。</p>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length == A[0].length &lt;= 100</code></li>
	<li><code>-100 &lt;= A[i][j] &lt;= 100</code></li>
</ol>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/minimum-falling-path-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-falling-path-sum/description/)

## 题解

类似于动态规划经典的数字三角形的问题。

记C(i, j)为从A(i, j)到最后一层的最小路径和。状态转移方程：

C(i, j) = min{ C(i+1, j-1), C(i+1, j), C(i+1, j+1) } + A(i, j)

对于最后一层，C(i, j) = A(i, j)。

最后求C(0, j)的最小值即可。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 88  ms | N/A |

```python3
class Solution:
    def minFallingPathSum(self, A):
        """
        :type A: List[List[int]]
        :rtype: int
        """
        if not A or not A[0]:
            return 0
        dp = [[0] * len(A[0]) for _ in range(len(A))]
        for j in range(len(A[0])):
            dp[-1][j] = A[-1][j]
        for i in range(len(A)-2, -1, -1):
            for j in range(len(A[0])):
                tmp = dp[i+1][j]
                if j > 0:
                    tmp = min(tmp, dp[i+1][j-1])
                if j < len(A) - 1:
                    tmp = min(tmp, dp[i+1][j+1])
                dp[i][j] = tmp + A[i][j]
        return min(dp[0])
```
