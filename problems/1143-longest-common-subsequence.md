## 1143. Longest Common Subsequence - 最长公共子序列

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个字符串&nbsp;<code>text1</code> 和&nbsp;<code>text2</code>，返回这两个字符串的最长公共子序列。</p>

<p>一个字符串的&nbsp;<em>子序列&nbsp;</em>是指这样一个新的字符串：它是由原字符串在不改变字符的相对顺序的情况下删除某些字符（也可以不删除任何字符）后组成的新字符串。<br>
例如，&quot;ace&quot; 是 &quot;abcde&quot; 的子序列，但 &quot;aec&quot; 不是 &quot;abcde&quot; 的子序列。两个字符串的「公共子序列」是这两个字符串所共同拥有的子序列。</p>

<p>若这两个字符串没有公共子序列，则返回 0。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入：</strong>text1 = &quot;abcde&quot;, text2 = &quot;ace&quot; 
<strong>输出：</strong>3  
<strong>解释：</strong>最长公共子序列是 &quot;ace&quot;，它的长度为 3。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入：</strong>text1 = &quot;abc&quot;, text2 = &quot;abc&quot;
<strong>输出：</strong>3
<strong>解释：</strong>最长公共子序列是 &quot;abc&quot;，它的长度为 3。
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入：</strong>text1 = &quot;abc&quot;, text2 = &quot;def&quot;
<strong>输出：</strong>0
<strong>解释：</strong>两个字符串没有公共子序列，返回 0。
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 &lt;= text1.length &lt;= 1000</code></li>
	<li><code>1 &lt;= text2.length &lt;= 1000</code></li>
	<li>输入的字符串只含有小写英文字符。</li>
</ul>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/longest-common-subsequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-common-subsequence/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 15 MB |

```cpp
class Solution {
public:
    int longestCommonSubsequence(string text1, string text2) {
        vector<vector<int>> dp(text1.length() + 1, vector<int>(text2.length() + 1));
        for (int i = 1; i <= (int)text1.length(); i++) {
            for (int j = 1; j <= (int)text2.length(); j++) {
                if (text1[i - 1] == text2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        return dp.back().back();
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
