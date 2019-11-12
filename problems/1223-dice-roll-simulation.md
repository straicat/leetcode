## 1223. Dice Roll Simulation - 掷骰子模拟

<!--If you want to use the English description, use `question.content` instead-->

<p>有一个骰子模拟器会每次投掷的时候生成一个 1 到 6 的随机数。</p>

<p>不过我们在使用它时有个约束，就是使得投掷骰子时，<strong>连续</strong> 掷出数字&nbsp;<code>i</code>&nbsp;的次数不能超过&nbsp;<code>rollMax[i]</code>（<code>i</code>&nbsp;从 1 开始编号）。</p>

<p>现在，给你一个整数数组&nbsp;<code>rollMax</code>&nbsp;和一个整数&nbsp;<code>n</code>，请你来计算掷&nbsp;<code>n</code>&nbsp;次骰子可得到的不同点数序列的数量。</p>

<p>假如两个序列中至少存在一个元素不同，就认为这两个序列是不同的。由于答案可能很大，所以请返回 <strong>模&nbsp;<code>10^9 + 7</code></strong>&nbsp;之后的结果。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>n = 2, rollMax = [1,1,2,2,2,3]
<strong>输出：</strong>34
<strong>解释：</strong>我们掷 2 次骰子，如果没有约束的话，共有 6 * 6 = 36 种可能的组合。但是根据 rollMax 数组，数字 1 和 2 最多连续出现一次，所以不会出现序列 (1,1) 和 (2,2)。因此，最终答案是 36-2 = 34。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>n = 2, rollMax = [1,1,1,1,1,1]
<strong>输出：</strong>30
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>n = 3, rollMax = [1,1,1,2,2,3]
<strong>输出：</strong>181
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 5000</code></li>
	<li><code>rollMax.length == 6</code></li>
	<li><code>1 &lt;= rollMax[i] &lt;= 15</code></li>
</ul>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/dice-roll-simulation/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/dice-roll-simulation/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 84  ms | 35.9 MB |

```cpp
class Solution {
public:
    int dieSimulator(int n, vector<int>& rollMax) {
        const int MOD = 1e9 + 7;
        vector<vector<vector<int>>> dp(n + 1, vector<vector<int>>(7, vector<int>(16)));
        // dp[i][j][k]: 第i次roll，结尾数字为j且结尾连续k次的数量
        dp[0][0][0] = 2;
        for (int j = 1; j <= 6; j++) {
            dp[0][j][0] = 1;
        }
        for (int i = 1; i <= n; i++) {
            long long  r = 0;
            for (int j = 1; j <= 6; j++) {
                long long m = 0;
                for (int k = 1; k <= min(15, i); k++) {
                    if (k > 1) {
                        dp[i][j][k] = rollMax[j - 1] >= k ? dp[i - 1][j][k - 1] : 0;
                    } else {
                        dp[i][j][k] = (MOD + dp[i - 1][0][0] - dp[i - 1][j][0]) % MOD;
                    }
                    m = (m + dp[i][j][k]) % MOD;
                }
                // 0位置用于保存求和结果
                dp[i][j][0] = m;
                r = (r + m) % MOD;
            }
            dp[i][0][0] = r;
        }
        // for (int i = 1; i <= n; i++) cout << dp[i][0][0] << " "; cout << endl;
        // for (int j = 1; j <= 6; j++) cout << dp[n][j][0] << " "; cout << endl;
        return dp[n][0][0];
    }
};
```
