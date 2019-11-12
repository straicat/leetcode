## 1218. Longest Arithmetic Subsequence of Given Difference - 最长定差子序列

<!--If you want to use the English description, use `question.content` instead-->

<p>给你一个整数数组&nbsp;<code>arr</code>&nbsp;和一个整数&nbsp;<code>difference</code>，请你找出&nbsp;<code>arr</code>&nbsp;中所有相邻元素之间的差等于给定&nbsp;<code>difference</code>&nbsp;的等差子序列，并返回其中最长的等差子序列的长度。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>arr = [1,2,3,4], difference = 1
<strong>输出：</strong>4
<strong>解释：</strong>最长的等差子序列是 [1,2,3,4]。</pre>

<p><strong>示例&nbsp;2：</strong></p>

<pre><strong>输入：</strong>arr = [1,3,5,7], difference = 1
<strong>输出：</strong>1
<strong>解释：</strong>最长的等差子序列是任意单个元素。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>arr = [1,5,7,8,5,3,4,2,1], difference = -2
<strong>输出：</strong>4
<strong>解释：</strong>最长的等差子序列是 [7,5,3,1]。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 10^5</code></li>
	<li><code>-10^4 &lt;= arr[i], difference &lt;= 10^4</code></li>
</ul>



-----

题目标签：Math / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/longest-arithmetic-subsequence-of-given-difference/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-arithmetic-subsequence-of-given-difference/description/)

## 题解

![TIM图片20191015012324](https://user-images.githubusercontent.com/9983385/66770539-77223800-eeea-11e9-8559-233238a0627c.jpg)

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 164  ms | 24.3 MB |

```cpp
class Solution {
public:
    int longestSubsequence(vector<int>& arr, int difference) {
        int n = arr.size();
        int num;
        unordered_map<int, int> pos;
        vector<int> dp(n, 1);
        int res = 0;
        for (int i = 0; i < n; i++) {
            num = arr[i];
            if (pos.find(num - difference) != pos.end()) {
                dp[i] += dp[pos[num - difference]];
            }
            pos[num] = i;
            res = max(res, dp[i]);
        }
        return res;
    }
};
```
