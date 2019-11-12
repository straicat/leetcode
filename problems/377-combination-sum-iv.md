## 377. Combination Sum IV - 组合总和 Ⅳ

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个由正整数组成且不存在重复数字的数组，找出和为给定目标正整数的组合的个数。</p>

<p><strong>示例:</strong></p>

<pre>
<em><strong>nums</strong></em> = [1, 2, 3]
<em><strong>target</strong></em> = 4

所有可能的组合为：
(1, 1, 1, 1)
(1, 1, 2)
(1, 2, 1)
(1, 3)
(2, 1, 1)
(2, 2)
(3, 1)

请注意，顺序不同的序列被视作不同的组合。

因此输出为 <strong>7</strong>。
</pre>

<p><strong>进阶：</strong><br />
如果给定的数组中含有负数会怎么样？<br />
问题会产生什么变化？<br />
我们需要在题目中添加什么限制来允许负数的出现？</p>

<p><strong>致谢：</strong><br />
特别感谢&nbsp;<a href="https://leetcode.com/pbrother/">@pbrother</a>&nbsp;添加此问题并创建所有测试用例。</p>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/combination-sum-iv/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combination-sum-iv/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 835.6 KB |

```cpp
class Solution {
public:
    int combinationSum4(vector<int>& nums, int target) {
        // dp[4] = dp[1] + dp[2] + dp[3] = 7
        // dp[1] = 1    dp[2] = dp[1] + 1 = 2    dp[3] = 1 + dp[1] + dp[2] = 4
        if (target == 0) {
            return 1;
        }
        if (nums.size() == 0) {
            return 0;
        }
        sort(nums.begin(), nums.end());
        vector<int> dp(target + 1, 0);
        for (int n : nums) {
            if (n <= target) {
                dp[n] = 1;
            }
        }
        for (int i = 0; i <= target; ++i) {
            for (int n : nums) {
                if (i > n) {
                    dp[i] += dp[i - n];
                } else {
                    break;
                }
            }
        }
        return dp[target];
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
