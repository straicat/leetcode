## 309. Best Time to Buy and Sell Stock with Cooldown - 最佳买卖股票时机含冷冻期

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组，其中第<em>&nbsp;i</em>&nbsp;个元素代表了第&nbsp;<em>i</em>&nbsp;天的股票价格 。​</p>

<p>设计一个算法计算出最大利润。在满足以下约束条件下，你可以尽可能地完成更多的交易（多次买卖一支股票）:</p>

<ul>
	<li>你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。</li>
	<li>卖出股票后，你无法在第二天买入股票 (即冷冻期为 1 天)。</li>
</ul>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,2,3,0,2]
<strong>输出: </strong>3 
<strong>解释:</strong> 对应的交易状态为: [买入, 卖出, 冷冻期, 买入, 卖出]</pre>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 1  ms | 36.8 MB |

```java
class Solution {
    public int maxProfit(int[] prices) {
        // 0: 买入, 1: 卖出, 2: 卖出第2天
        int[][] dp = new int[prices.length + 1][3];
        dp[0][0] = Integer.MIN_VALUE;
        for (int i = 1; i <= prices.length; i++) {
            dp[i][0] = Math.max(dp[i - 1][0], dp[i - 1][2] - prices[i - 1]);
            dp[i][1] = dp[i - 1][0] + prices[i - 1];
            dp[i][2] = Math.max(dp[i - 1][2], dp[i - 1][1]);
        }
        return Math.max(dp[prices.length][1], dp[prices.length][2]);
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1 MB |

```cpp
// refer: https://www.bilibili.com/video/av31578180
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        /*
              hold -> sell      hold -> hold      check ways into hold: hold[i] = max(hold[i-1], rest[i-1] - prices[i])
              sell -> rest                        check ways into sell: sell[i] = hold[i-1] + prices[i]
              rest -> hold      rest -> rest      check ways into rest: rest[i] = max(rest[i-1], sell[i-1])
        */
        int hold = INT_MIN;
        int sell = 0;
        int rest = 0;
        for (int price : prices) {
            int tmp = rest;  // rest[i-1]
            rest = max(rest, sell);  // rest[i]
            sell = hold + price;  // sell[i]
            hold = max(hold, tmp - price);  // hold[i]
        }
        return max(sell, rest);
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
