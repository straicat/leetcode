## 1021. Remove Outermost Parentheses - 删除最外层的括号

<!--If you want to use the English description, use `question.content` instead-->

<p>有效括号字符串为空&nbsp;<code>(&quot;&quot;)</code>、<code>&quot;(&quot; + A + &quot;)&quot;</code>&nbsp;或&nbsp;<code>A + B</code>，其中&nbsp;<code>A</code> 和&nbsp;<code>B</code>&nbsp;都是有效的括号字符串，<code>+</code>&nbsp;代表字符串的连接。例如，<code>&quot;&quot;</code>，<code>&quot;()&quot;</code>，<code>&quot;(())()&quot;</code>&nbsp;和&nbsp;<code>&quot;(()(()))&quot;</code>&nbsp;都是有效的括号字符串。</p>

<p>如果有效字符串&nbsp;<code>S</code>&nbsp;非空，且不存在将其拆分为&nbsp;<code>S = A+B</code>&nbsp;的方法，我们称其为<strong>原语（primitive）</strong>，其中&nbsp;<code>A</code> 和&nbsp;<code>B</code>&nbsp;都是非空有效括号字符串。</p>

<p>给出一个非空有效字符串&nbsp;<code>S</code>，考虑将其进行原语化分解，使得：<code>S = P_1 + P_2 + ... + P_k</code>，其中&nbsp;<code>P_i</code>&nbsp;是有效括号字符串原语。</p>

<p>对&nbsp;<code>S</code>&nbsp;进行原语化分解，删除分解中每个原语字符串的最外层括号，返回 <code>S</code>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>&quot;(()())(())&quot;
<strong>输出：</strong>&quot;()()()&quot;
<strong>解释：
</strong>输入字符串为 &quot;(()())(())&quot;，原语化分解得到 &quot;(()())&quot; + &quot;(())&quot;，
删除每个部分中的最外层括号后得到 &quot;()()&quot; + &quot;()&quot; = &quot;()()()&quot;。</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>&quot;(()())(())(()(()))&quot;
<strong>输出：</strong>&quot;()()()()(())&quot;
<strong>解释：</strong>
输入字符串为 &quot;(()())(())(()(()))&quot;，原语化分解得到 &quot;(()())&quot; + &quot;(())&quot; + &quot;(()(()))&quot;，
删除每隔部分中的最外层括号后得到 &quot;()()&quot; + &quot;()&quot; + &quot;()(())&quot; = &quot;()()()()(())&quot;。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>&quot;()()&quot;
<strong>输出：</strong>&quot;&quot;
<strong>解释：</strong>
输入字符串为 &quot;()()&quot;，原语化分解得到 &quot;()&quot; + &quot;()&quot;，
删除每个部分中的最外层括号后得到 &quot;&quot; + &quot;&quot; = &quot;&quot;。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>S.length &lt;= 10000</code></li>
	<li><code>S[i]</code> 为&nbsp;<code>&quot;(&quot;</code> 或&nbsp;<code>&quot;)&quot;</code></li>
	<li><code>S</code> 是一个有效括号字符串</li>
</ol>



-----

题目标签：Stack

题目链接：[LeetCode](https://leetcode.com/problems/remove-outermost-parentheses/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-outermost-parentheses/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 44  ms | 12.9 MB |

```python3
class Solution:
    def removeOuterParentheses(self, S: str) -> str:
        left = 0
        right = 0
        tmp = ''
        res = ''
        for c in S:
            tmp += c
            if c == '(':
                left += 1
            else:
                right += 1
                if left == right:
                    res += tmp[1:-1]
                    tmp = ''
        return res
```
