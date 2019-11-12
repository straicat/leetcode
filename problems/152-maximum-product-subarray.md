## 152. Maximum Product Subarray - 乘积最大子序列

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组 <code>nums</code>&nbsp;，找出一个序列中乘积最大的连续子序列（该序列至少包含一个数）。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [2,3,-2,4]
<strong>输出:</strong> <code>6</code>
<strong>解释:</strong>&nbsp;子数组 [2,3] 有最大乘积 6。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [-2,0,-1]
<strong>输出:</strong> 0
<strong>解释:</strong>&nbsp;结果不能为 2, 因为 [-2,-1] 不是子数组。</pre>



-----

题目标签：Array / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/maximum-product-subarray/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-product-subarray/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1.4 MB |

```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        if (nums.size() == 0) return 0;
        vector<int> dp(nums.size(), 0);
        dp[0] = nums[0];
        int pre = nums[0] < 0 ? 0 : -1;
        for (int i=1; i<nums.size(); ++i) {
            if (nums[i] >= 0) {
                dp[i] = max(nums[i], nums[i] * dp[i-1]);
            } else {
                if (pre != -1) {
                    int k = 1;
                    for (int j=pre; j<=i; ++j) {
                        k *= nums[j];
                    }
                    dp[i] = max(k, k * dp[pre-1]);
                }
                pre = i;
            }
        }
        return *max_element(dp.begin(), dp.end());
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
