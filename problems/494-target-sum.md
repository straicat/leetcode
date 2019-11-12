## 494. Target Sum - 目标和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非负整数数组，a1, a2, ..., an, 和一个目标数，S。现在你有两个符号&nbsp;<code>+</code>&nbsp;和&nbsp;<code>-</code>。对于数组中的任意一个整数，你都可以从&nbsp;<code>+</code>&nbsp;或&nbsp;<code>-</code>中选择一个符号添加在前面。</p>

<p>返回可以使最终数组和为目标数 S 的所有添加符号的方法数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> nums: [1, 1, 1, 1, 1], S: 3
<strong>输出:</strong> 5
<strong>解释:</strong> 

-1+1+1+1+1 = 3
+1-1+1+1+1 = 3
+1+1-1+1+1 = 3
+1+1+1-1+1 = 3
+1+1+1+1-1 = 3

一共有5种方法让最终目标和为3。
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>数组非空，且长度不会超过20。</li>
	<li>初始的数组的和不会超过1000。</li>
	<li>保证返回的最终结果能被32位整数存下。</li>
</ol>



-----

题目标签：Depth-first Search / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/target-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/target-sum/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 544  ms | 1.4 MB |

```cpp
class Solution {
public:
    int res = 0;
    void dfs(vector<int>& nums, int s, int i) {
        if (i == nums.size()) {
            res += !s;
            return;
        }
        dfs(nums, s-nums[i], i+1);
        dfs(nums, s+nums[i], i+1);
    }

    int findTargetSumWays(vector<int>& nums, int S) {
        dfs(nums, S, 0);
        return res;
    }
};
```
