## 942. DI String Match - 增减字符串匹配

<!--If you want to use the English description, use `question.content` instead-->

<p>给定只含&nbsp;<code>&quot;I&quot;</code>（增大）或 <code>&quot;D&quot;</code>（减小）的字符串&nbsp;<code>S</code>&nbsp;，令&nbsp;<code>N = S.length</code>。</p>

<p>返回&nbsp;<code>[0, 1, ..., N]</code>&nbsp;的任意排列&nbsp;<code>A</code>&nbsp;使得对于所有&nbsp;<code>i = 0,&nbsp;..., N-1</code>，都有：</p>

<ul>
	<li>如果&nbsp;<code>S[i] == &quot;I&quot;</code>，那么&nbsp;<code>A[i] &lt; A[i+1]</code></li>
	<li>如果&nbsp;<code>S[i] == &quot;D&quot;</code>，那么&nbsp;<code>A[i] &gt; A[i+1]</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输出：</strong>&quot;IDID&quot;
<strong>输出：</strong>[0,4,1,3,2]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输出：</strong>&quot;III&quot;
<strong>输出：</strong>[0,1,2,3]
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输出：</strong>&quot;DDI&quot;
<strong>输出：</strong>[3,2,0,1]</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= S.length &lt;= 1000</code></li>
	<li><code>S</code> 只包含字符&nbsp;<code>&quot;I&quot;</code>&nbsp;或&nbsp;<code>&quot;D&quot;</code>。</li>
</ol>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/di-string-match/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/di-string-match/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 92  ms | 14.3 MB |

```python3
class Solution:
    def diStringMatch(self, S: str) -> List[int]:
        A = [x for x in range(len(S) + 1)]
        res = []
        p, q = 0, len(S)
        for i in range(len(S)):
            if S[i] == 'I':
                res.append(A[p])
                p += 1
            else:
                res.append(A[q])
                q -= 1
        res.append(A[p])
        return res
```
