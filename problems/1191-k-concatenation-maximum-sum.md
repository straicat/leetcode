## 1191. K-Concatenation Maximum Sum - K 次串联后最大子数组之和

<!--If you want to use the English description, use `question.content` instead-->

<p>给你一个整数数组&nbsp;<code>arr</code>&nbsp;和一个整数&nbsp;<code>k</code>。</p>

<p>首先，我们要对该数组进行修改，即把原数组 <code>arr</code> 重复&nbsp;<code>k</code>&nbsp;次。</p>

<blockquote>
<p>举个例子，如果&nbsp;<code>arr&nbsp;= [1, 2]</code> 且 <code>k = 3</code>，那么修改后的数组就是&nbsp;<code>[1, 2, 1, 2, 1, 2]</code>。</p>
</blockquote>

<p>然后，请你返回修改后的数组中的最大的子数组之和。</p>

<p>注意，子数组长度可以是 <code>0</code>，在这种情况下它的总和也是 <code>0</code>。</p>

<p>由于&nbsp;<strong>结果可能会很大</strong>，所以需要 <strong>模（mod）</strong>&nbsp;<code>10^9 + 7</code>&nbsp;后再返回。&nbsp;</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>arr = [1,2], k = 3
<strong>输出：</strong>9
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>arr = [1,-2,1], k = 5
<strong>输出：</strong>2
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>arr = [-1,-2], k = 7
<strong>输出：</strong>0
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 10^5</code></li>
	<li><code>1 &lt;= k &lt;= 10^5</code></li>
	<li><code>-10^4 &lt;= arr[i] &lt;= 10^4</code></li>
</ul>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/k-concatenation-maximum-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/k-concatenation-maximum-sum/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 380  ms | 27.2 MB |

```python3
class Solution:
    def kConcatenationMaxSum(self, arr: List[int], k: int) -> int:
        s = sum(arr)
        if s > 0:
            t = 0
            m1 = -1e20
            for a in arr:
                t += a
                m1 = t if t > m1 else m1
            t = 0
            m2 = -1e20
            for a in arr[::-1]:
                t += a
                m2 = t if t > m2 else m2
            if k > 1:
                return (m1 + m2 + s * (k - 2)) % 1000000007
            else:
                t = 0
                l = len(arr)
                r = -1e20
                for i in range(l):
                    if i == 0:
                        t = arr[i]
                    else:
                        if t > 0:
                            t = t + arr[i]
                        else:
                            t = arr[i]
                    r = max(r, t)
                return r % 1000000007
        elif s < 0:
            t = 0
            l = len(arr)
            r = -1e20
            for i in range(2 * l):
                if i == 0:
                    t = arr[i]
                else:
                    if t > 0:
                        t = t + arr[i % l]
                    else:
                        t = arr[i % l]
                r = max(r, t)
            return max(0, r)
        else:
            t = 0
            mi = 1e20
            ma = -1e20
            for a in arr:
                t += a
                mi = t if t < mi else mi
                ma = t if t > ma else ma
            return (ma - mi) % 1000000007
```
