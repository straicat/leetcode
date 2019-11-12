## 1190. Reverse Substrings Between Each Pair of Parentheses - 反转每对括号间的子串

<!--If you want to use the English description, use `question.content` instead-->

<p>给出一个字符串&nbsp;<code>s</code>（仅含有小写英文字母和括号）。</p>

<p>请你按照从括号内到外的顺序，逐层反转每对匹配括号中的字符串，并返回最终的结果。</p>

<p>注意，您的结果中 <strong>不应</strong> 包含任何括号。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = &quot;(abcd)&quot;
<strong>输出：</strong>&quot;dcba&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>s = &quot;(u(love)i)&quot;
<strong>输出：</strong>&quot;iloveu&quot;
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>s = &quot;(ed(et(oc))el)&quot;
<strong>输出：</strong>&quot;leetcode&quot;
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>s = &quot;a(bcdefghijkl(mno)p)q&quot;
<strong>输出：</strong>&quot;apmnolkjihgfedcbq&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 2000</code></li>
	<li><code>s</code> 中只有小写英文字母和括号</li>
	<li>我们确保所有括号都是成对出现的</li>
</ul>



-----

题目标签：Stack

题目链接：[LeetCode](https://leetcode.com/problems/reverse-substrings-between-each-pair-of-parentheses/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-substrings-between-each-pair-of-parentheses/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 9.4 MB |

```cpp
class Solution {
public:
    string reverseParentheses(string s) {
        stack<char> stk;
        for (char c : s) {
            if (c == '(') {
                stk.push(c);
            } else if (c == ')') {
                queue<char> tmp;
                while (stk.top() != '(') {
                    tmp.push(stk.top());
                    stk.pop();
                }
                stk.pop();
                while (!tmp.empty()) {
                    stk.push(tmp.front());
                    tmp.pop();
                }
            } else {
                stk.push(c);
            }
        }
        string ss;
        while (!stk.empty()) {
            ss += stk.top();
            stk.pop();
        }
        reverse(ss.begin(), ss.end());
        return ss;
    }
};
```
