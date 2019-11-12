## 300. Longest Increasing Subsequence - 最长上升子序列

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个无序的整数数组，找到其中最长上升子序列的长度。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> <code>[10,9,2,5,3,7,101,18]
</code><strong>输出: </strong>4 
<strong>解释: </strong>最长的上升子序列是&nbsp;<code>[2,3,7,101]，</code>它的长度是 <code>4</code>。</pre>

<p><strong>说明:</strong></p>

<ul>
	<li>可能会有多种最长上升子序列的组合，你只需要输出对应的长度即可。</li>
	<li>你算法的时间复杂度应该为&nbsp;O(<em>n<sup>2</sup></em>) 。</li>
</ul>

<p><strong>进阶:</strong> 你能将算法的时间复杂度降低到&nbsp;O(<em>n</em> log <em>n</em>) 吗?</p>



-----

题目标签：Binary Search / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/longest-increasing-subsequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-increasing-subsequence/description/)

## 题解

可以使用动态规划。`dp`数组记录以当前数字结束的最长上升子序列长度。对于每个数字`nums[i]`，查看其左侧比它小的数字`nums[j]`，状态转移方程：`dp[i] = max(dp[i], 1+dp[j])`。时间复杂度O(N^2)



二分法。维护一个数组`rec`，该数组第`i`个元素记录长度为`i+1`的上升子序列末端最小数字。对于每个数字`num`，与该数组末端的数字`back`进行比较，如果`num > back`，则将`num`加入该数组`rec`的末端；否则，在数组`rec`中二分查找最小的比`num`大的元素，并以`num`替换之。最后，最长上升子序列的长度就是`rec`的长度。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 8.8 MB |

```cpp
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        if (!nums.size()) return 0;
        vector<int> ret;
        ret.push_back(nums[0]);
        for (int i = 1; i < nums.size(); i++) {
            if (nums[i] > ret.back()) 
                ret.push_back(nums[i]);
            else
                ret[lower_bound(ret.begin(), ret.end(), nums[i]) - ret.begin()] = nums[i];
        }
        return ret.size();
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
