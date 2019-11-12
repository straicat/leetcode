## 213. House Robber II - 打家劫舍 II

<!--If you want to use the English description, use `question.content` instead-->

<p>你是一个专业的小偷，计划偷窃沿街的房屋，每间房内都藏有一定的现金。这个地方所有的房屋都<strong>围成一圈，</strong>这意味着第一个房屋和最后一个房屋是紧挨着的。同时，相邻的房屋装有相互连通的防盗系统，<strong>如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警</strong>。</p>

<p>给定一个代表每个房屋存放金额的非负整数数组，计算你<strong>在不触动警报装置的情况下，</strong>能够偷窃到的最高金额。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [2,3,2]
<strong>输出:</strong> 3
<strong>解释:</strong> 你不能先偷窃 1 号房屋（金额 = 2），然后偷窃 3 号房屋（金额 = 2）, 因为他们是相邻的。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [1,2,3,1]
<strong>输出:</strong> 4
<strong>解释:</strong> 你可以先偷窃 1 号房屋（金额 = 1），然后偷窃 3 号房屋（金额 = 3）。
&nbsp;    偷窃到的最高金额 = 1 + 3 = 4 。</pre>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/house-robber-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/house-robber-ii/description/)

## 题解

转为House Robber子问题，分抢第0家和抢最后一家两种，然后取大者。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 880.6 KB |

```cpp
class Solution {
public:
    int robSub(vector<int>& nums, int st, int ed) {
        if (ed == st) return 0;
        vector<int> dp = vector<int>(ed - st + 2, 0);
        for (int i=0; i<ed - st; ++i) {
            dp[i+2] = max(dp[i+1], nums[i+st] + dp[i]);
        }
        return dp.back();
    }

    int rob(vector<int>& nums) {
        if (nums.size() == 0) return 0;
        if (nums.size() <= 3) return *max_element(nums.begin(), nums.end());
        return max(robSub(nums, 0, nums.size()-1), robSub(nums, 1, nums.size()));
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
