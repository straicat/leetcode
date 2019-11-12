## 322. Coin Change - 零钱兑换

<!--If you want to use the English description, use `question.content` instead-->

<p>给定不同面额的硬币 coins 和一个总金额 amount。编写一个函数来计算可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，返回&nbsp;<code>-1</code>。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入: </strong>coins = <code>[1, 2, 5]</code>, amount = <code>11</code>
<strong>输出: </strong><code>3</code> 
<strong>解释:</strong> 11 = 5 + 5 + 1</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>coins = <code>[2]</code>, amount = <code>3</code>
<strong>输出: </strong>-1</pre>

<p><strong>说明</strong>:<br>
你可以认为每种硬币的数量是无限的。</p>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/coin-change/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/coin-change/description/)

## 题解

1、动态规划

初始状态：`dp[i] = INT_MAX, dp[0] = 0`

状态转移：”` dp[i] = min(dp[i], dp[i - coin] + 1)`

注意int溢出。



2、搜索+剪枝

使用搜索算法，尽量使用大额硬币。注意剪枝：如果是最小面额，检查能否整除剩余金额；每次递归前，只有比当前最优解更好才进行递归，否则跳出（剪枝，这步剪枝很关键）。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 856.1 KB |

```cpp
// refer: https://www.bilibili.com/video/av31621107
class Solution {
public:
    void backTacking(vector<int>& coins, int amount, int index, int cur, int& res) {
        int coin = coins[index];
        if (index == 0) {
            if (amount % coin == 0) {
                res = min(res, cur + amount / coin);
            }
        } else {
            for (int n = amount / coin; n >= 0 && cur + n < res; --n) {
                backTacking(coins, amount - n * coin, index - 1, cur + n, res);
            }
        }
    }

    int coinChange(vector<int>& coins, int amount) {
        sort(coins.begin(), coins.end());
        int res = INT_MAX;
        backTacking(coins, amount, coins.size() - 1, 0, res);
        return res == INT_MAX ? -1 : res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
