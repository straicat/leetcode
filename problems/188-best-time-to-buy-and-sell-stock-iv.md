## 188. Best Time to Buy and Sell Stock IV - 买卖股票的最佳时机 IV

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个数组，它的第<em> i</em> 个元素是一支给定的股票在第 <em>i </em>天的价格。</p>

<p>设计一个算法来计算你所能获取的最大利润。你最多可以完成 <strong>k</strong> 笔交易。</p>

<p><strong>注意:</strong>&nbsp;你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [2,4,1], k = 2
<strong>输出:</strong> 2
<strong>解释:</strong> 在第 1 天 (股票价格 = 2) 的时候买入，在第 2 天 (股票价格 = 4) 的时候卖出，这笔交易所能获得利润 = 4-2 = 2 。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [3,2,6,5,0,3], k = 2
<strong>输出:</strong> 7
<strong>解释:</strong> 在第 2 天 (股票价格 = 2) 的时候买入，在第 3 天 (股票价格 = 6) 的时候卖出, 这笔交易所能获得利润 = 6-2 = 4 。
&nbsp;    随后，在第 5 天 (股票价格 = 0) 的时候买入，在第 6 天 (股票价格 = 3) 的时候卖出, 这笔交易所能获得利润 = 3-0 = 3 。
</pre>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-iv/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 8  ms | 36.1 MB |

```java
class Solution {
    public int maxProfit(int k, int[] prices) {
        if (k >= prices.length / 2) {
            int[][] dp = new int[prices.length + 1][2];
            dp[0][0] = Integer.MIN_VALUE;

            for (int i = 1; i <= prices.length; i++) {
                dp[i][0] = Math.max(dp[i - 1][0], dp[i - 1][1] - prices[i - 1]);
                dp[i][1] = Math.max(dp[i - 1][1], dp[i - 1][0] + prices[i - 1]);
            }
            return dp[prices.length][1];
        }
        int[][][] dp = new int[prices.length + 1][k + 1][2];
        int res = 0;
        for (int j = 0; j <= k; j++) {
            for (int i = 0; i <= prices.length; i++) {
                if (i == 0 || j == 0) {
                    dp[i][j][0] = Integer.MIN_VALUE;
                    continue;
                }
                dp[i][j][0] = Math.max(dp[i - 1][j][0], dp[i - 1][j - 1][1] - prices[i - 1]);
                res = Math.max(res, dp[i][j][1] = Math.max(dp[i - 1][j][1], dp[i - 1][j][0] + prices[i - 1]));
            }
        }
        return res;
    }
}
```
