## 32. Longest Valid Parentheses - 最长有效括号

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个只包含 <code>&#39;(&#39;</code>&nbsp;和 <code>&#39;)&#39;</code>&nbsp;的字符串，找出最长的包含有效括号的子串的长度。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> &quot;(()&quot;
<strong>输出:</strong> 2
<strong>解释:</strong> 最长有效括号子串为 <code>&quot;()&quot;</code>
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> &quot;<code>)()())</code>&quot;
<strong>输出:</strong> 4
<strong>解释:</strong> 最长有效括号子串为 <code>&quot;()()&quot;</code>
</pre>



-----

题目标签：String / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/longest-valid-parentheses/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-valid-parentheses/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 9.6 MB |

```cpp
class Solution {
public:
    int longestValidParentheses(string s) {
        int n = s.length();
        vector<int> dp(n);
        int t, res = 0;
        for (int i = 0; i < n; i++) {
            char c = s[i];
            if (c == ')') {
                if (i && s[i - 1] == '(') {
                    dp[i] = (i > 1 ? dp[i - 2] : 0) + 2;
                } else if (i > 1 && (t = i - dp[i - 1] - 1) >= 0 && t < n && s[t] == '(') {
                    dp[i] = (t > 1 ? dp[t - 1] : 0) + dp[i - 1] + 2;
                }
                res = max(res, dp[i]);
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
