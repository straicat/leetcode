## 198. House Robber - 打家劫舍

<!--If you want to use the English description, use `question.content` instead-->

<p>你是一个专业的小偷，计划偷窃沿街的房屋。每间房内都藏有一定的现金，影响你偷窃的唯一制约因素就是相邻的房屋装有相互连通的防盗系统，<strong>如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警</strong>。</p>

<p>给定一个代表每个房屋存放金额的非负整数数组，计算你<strong>在不触动警报装置的情况下，</strong>能够偷窃到的最高金额。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,2,3,1]
<strong>输出:</strong> 4
<strong>解释:</strong> 偷窃 1 号房屋 (金额 = 1) ，然后偷窃 3 号房屋 (金额 = 3)。
&nbsp;    偷窃到的最高金额 = 1 + 3 = 4 。</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [2,7,9,3,1]
<strong>输出:</strong> 12
<strong>解释:</strong> 偷窃 1 号房屋 (金额 = 2), 偷窃 3 号房屋 (金额 = 9)，接着偷窃 5 号房屋 (金额 = 1)。
&nbsp;    偷窃到的最高金额 = 2 + 9 + 1 = 12 。
</pre>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/house-robber/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/house-robber/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 864.3 KB |

```cpp
class Solution {
public:
    int rob(vector<int>& nums) {
        if (nums.size() == 0) return 0;
        vector<int> dp = vector<int>(nums.size() + 2, 0);
        for (int i=0; i<nums.size(); ++i) {
            dp[i+2] = max(dp[i+1], nums[i] + dp[i]);
        }
        return dp.back();
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
