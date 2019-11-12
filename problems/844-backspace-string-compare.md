## 844. Backspace String Compare - 比较含退格的字符串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定 <code>S</code> 和 <code>T</code> 两个字符串，当它们分别被输入到空白的文本编辑器后，判断二者是否相等，并返回结果。 <code>#</code> 代表退格字符。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>S = &quot;ab#c&quot;, T = &quot;ad#c&quot;
<strong>输出：</strong>true
<strong>解释：</strong>S 和 T 都会变成 &ldquo;ac&rdquo;。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>S = &quot;ab##&quot;, T = &quot;c#d#&quot;
<strong>输出：</strong>true
<strong>解释：</strong>S 和 T 都会变成 &ldquo;&rdquo;。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>S = &quot;a##c&quot;, T = &quot;#a#c&quot;
<strong>输出：</strong>true
<strong>解释：</strong>S 和 T 都会变成 &ldquo;c&rdquo;。
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>S = &quot;a#c&quot;, T = &quot;b&quot;
<strong>输出：</strong>false
<strong>解释：</strong>S 会变成 &ldquo;c&rdquo;，但 T 仍然是 &ldquo;b&rdquo;。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= S.length &lt;= 200</code></li>
	<li><code>1 &lt;= T.length &lt;= 200</code></li>
	<li><code>S</code> 和 <code>T</code> 只含有小写字母以及字符 <code>&#39;#&#39;</code>。</li>
</ol>

<p>&nbsp;</p>



-----

题目标签：Stack / Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/backspace-string-compare/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/backspace-string-compare/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 8.7 MB |

```cpp
class Solution {
public:
    void toStack(string& s, stack<char>& stk) {
        for (char c : s) {
            if (c == '#') {
                if (!stk.empty()) {
                    stk.pop();
                }
            } else {
                stk.push(c);
            }
        }
    }
    
    bool backspaceCompare(string S, string T) {
        stack<char> ss, st;
        toStack(S, ss);
        toStack(T, st);
        while (!ss.empty() && !st.empty()) {
            char a = ss.top(); ss.pop();
            char b = st.top(); st.pop();
            if (a != b) return false;
        }
        if (ss.empty() && st.empty()) return true;
        else return false;
    }
};
```
