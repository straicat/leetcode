## 375. Guess Number Higher or Lower II - 猜数字大小 II

<!--If you want to use the English description, use `question.content` instead-->

<p>我们正在玩一个猜数游戏，游戏规则如下：</p>

<p>我从&nbsp;<strong>1&nbsp;</strong>到 <strong>n</strong> 之间选择一个数字，你来猜我选了哪个数字。</p>

<p>每次你猜错了，我都会告诉你，我选的数字比你的大了或者小了。</p>

<p>然而，当你猜了数字 x 并且猜错了的时候，你需要支付金额为 x 的现金。直到你猜到我选的数字，你才算赢得了这个游戏。</p>

<p><strong>示例:</strong></p>

<pre>n = 10, 我选择了8.

第一轮: 你猜我选择的数字是5，我会告诉你，我的数字更大一些，然后你需要支付5块。
第二轮: 你猜是7，我告诉你，我的数字更大一些，你支付7块。
第三轮: 你猜是9，我告诉你，我的数字更小一些，你支付9块。

游戏结束。8 就是我选的数字。

你最终要支付 5 + 7 + 9 = 21 块钱。
</pre>

<p>给定&nbsp;<strong>n &ge; 1，</strong>计算你至少需要拥有多少现金才能确保你能赢得这个游戏。</p>



-----

题目标签：Minimax / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/guess-number-higher-or-lower-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/guess-number-higher-or-lower-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1 MB |

```cpp
class Solution {
public:
    vector<vector<int> > dp;

    int dfs(int l, int r) {
        // no need to guess
        if (l >= r) {
            return 0;
        }
        // judge corner cases first!
        // Line 781: Char 41: runtime error: reference binding to misaligned address 0x000000000051 for type 'value_type', which requires 4 byte alignment (stl_vector.h)
        // reason: calculate right cost before left cost and return dp[l][r] before judge corner cases(l >= r)
        // it has been processed
        if (dp[l][r] != -1) {
            return dp[l][r];
        }
        // initialized to a maximum value because it is to be minimized
        dp[l][r] = INT_MAX;
        // state transition equation:
        // dp[l][r] = min( i + dp[l][i-1] + dp[i+1][r] )   , i from l to r
        // start with guess i
        // just need to guess from r to mid
        for (int i = r; i >= l + (r - l) / 2; --i) {
            int cost = i;
            // optimize with pruning
            if (cost < dp[l][r]) {
                int left = dfs(l, i - 1);
                if (cost + left < dp[l][r]) {
                    int right = dfs(i + 1, r);
                    // only need to pay the money for one side
                    // because it's unnecessary to guess another side
                    cost += max(left, right);
                    dp[l][r] = min(dp[l][r], cost);
                }
            }
        }
        return dp[l][r];
    }

    int getMoneyAmount(int n) {
        dp = vector<vector<int> >(n + 1, vector<int>(n + 1, -1));
        return dfs(1, n);
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
