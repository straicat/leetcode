## 926. Flip String to Monotone Increasing - 将字符串翻转到单调递增

<!--If you want to use the English description, use `question.content` instead-->

<p>如果一个由&nbsp;<code>&#39;0&#39;</code> 和 <code>&#39;1&#39;</code>&nbsp;组成的字符串，是以一些 <code>&#39;0&#39;</code>（可能没有 <code>&#39;0&#39;</code>）后面跟着一些 <code>&#39;1&#39;</code>（也可能没有 <code>&#39;1&#39;</code>）的形式组成的，那么该字符串是<em>单调递增</em>的。</p>

<p>我们给出一个由字符 <code>&#39;0&#39;</code> 和 <code>&#39;1&#39;</code>&nbsp;组成的字符串&nbsp;<code>S</code>，我们可以将任何&nbsp;<code>&#39;0&#39;</code> 翻转为&nbsp;<code>&#39;1&#39;</code>&nbsp;或者将&nbsp;<code>&#39;1&#39;</code>&nbsp;翻转为&nbsp;<code>&#39;0&#39;</code>。</p>

<p>返回使 <code>S</code> 单调递增的最小翻转次数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>&quot;00110&quot;
<strong>输出：</strong>1
<strong>解释：</strong>我们翻转最后一位得到 00111.
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>&quot;010110&quot;
<strong>输出：</strong>2
<strong>解释：</strong>我们翻转得到 011111，或者是 000111。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>&quot;00011000&quot;
<strong>输出：</strong>2
<strong>解释：</strong>我们翻转得到 00000000。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= S.length &lt;= 20000</code></li>
	<li><code>S</code> 中只包含字符&nbsp;<code>&#39;0&#39;</code>&nbsp;和&nbsp;<code>&#39;1&#39;</code></li>
</ol>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/flip-string-to-monotone-increasing/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/flip-string-to-monotone-increasing/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 64  ms | N/A |

```python3
class Solution:
    def minFlipsMonoIncr(self, S):
        """
        :type S: str
        :rtype: int
        """
        a = S.count('0')
        b = S.count('1')
        if a == 0 or b == 0:
            return 0
        dp = [0] * (a+b+1)
        dp[0] = a
        lf = 0
        rf = a
        for i, s in enumerate(S):
            if s == '1':
                lf += 1
            else:
                rf -= 1
            dp[i+1] = lf + rf
        return min(dp)
```
