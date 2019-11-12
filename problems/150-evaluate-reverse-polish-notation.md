## 150. Evaluate Reverse Polish Notation - 逆波兰表达式求值

<!--If you want to use the English description, use `question.content` instead-->

<p>根据<a href="https://baike.baidu.com/item/%E9%80%86%E6%B3%A2%E5%85%B0%E5%BC%8F/128437" target="_blank">逆波兰表示法</a>，求表达式的值。</p>

<p>有效的运算符包括&nbsp;<code>+</code>,&nbsp;<code>-</code>,&nbsp;<code>*</code>,&nbsp;<code>/</code>&nbsp;。每个运算对象可以是整数，也可以是另一个逆波兰表达式。</p>

<p><strong>说明：</strong></p>

<ul>
	<li>整数除法只保留整数部分。</li>
	<li>给定逆波兰表达式总是有效的。换句话说，表达式总会得出有效数值且不存在除数为 0 的情况。</li>
</ul>

<p><strong>示例&nbsp;1：</strong></p>

<pre><strong>输入:</strong> [&quot;2&quot;, &quot;1&quot;, &quot;+&quot;, &quot;3&quot;, &quot;*&quot;]
<strong>输出:</strong> 9
<strong>解释:</strong> ((2 + 1) * 3) = 9
</pre>

<p><strong>示例&nbsp;2：</strong></p>

<pre><strong>输入:</strong> [&quot;4&quot;, &quot;13&quot;, &quot;5&quot;, &quot;/&quot;, &quot;+&quot;]
<strong>输出:</strong> 6
<strong>解释:</strong> (4 + (13 / 5)) = 6
</pre>

<p><strong>示例&nbsp;3：</strong></p>

<pre><strong>输入:</strong> [&quot;10&quot;, &quot;6&quot;, &quot;9&quot;, &quot;3&quot;, &quot;+&quot;, &quot;-11&quot;, &quot;*&quot;, &quot;/&quot;, &quot;*&quot;, &quot;17&quot;, &quot;+&quot;, &quot;5&quot;, &quot;+&quot;]
<strong>输出:</strong> 22
<strong>解释:</strong> 
  ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22</pre>



-----

题目标签：Stack

题目链接：[LeetCode](https://leetcode.com/problems/evaluate-reverse-polish-notation/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/evaluate-reverse-polish-notation/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 2.4 MB |

```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        vector<int> v;
        for (string t : tokens) {
            if (t.size() == 1 && (t == "+" || t == "-" || t == "*" || t == "/")) {
                int n2 = v.back();
                v.pop_back();
                int n1 = v.back();
                v.pop_back();
                switch (t[0]) {  // Note: switch quantity must be an integer
                    case '+': v.push_back(n1 + n2); break;  // Note: need break
                    case '-': v.push_back(n1 - n2); break;
                    case '*': v.push_back(n1 * n2); break;
                    case '/': v.push_back(n1 / n2); break;
                }
            } else {
                v.push_back(stoi(t));
            }
        }
        return v.back();
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
