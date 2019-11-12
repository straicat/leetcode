## 227. Basic Calculator II - 基本计算器 II

<!--If you want to use the English description, use `question.content` instead-->

<p>实现一个基本的计算器来计算一个简单的字符串表达式的值。</p>

<p>字符串表达式仅包含非负整数，<code>+</code>， <code>-</code> ，<code>*</code>，<code>/</code> 四种运算符和空格&nbsp;<code>&nbsp;</code>。 整数除法仅保留整数部分。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入: </strong>&quot;3+2*2&quot;
<strong>输出:</strong> 7
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> &quot; 3/2 &quot;
<strong>输出:</strong> 1</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> &quot; 3+5 / 2 &quot;
<strong>输出:</strong> 5
</pre>

<p><strong>说明：</strong></p>

<ul>
	<li>你可以假设所给定的表达式都是有效的。</li>
	<li>请<strong>不要</strong>使用内置的库函数 <code>eval</code>。</li>
</ul>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/basic-calculator-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/basic-calculator-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 1.8 MB |

```cpp
class Solution {
public:
    vector<int> nums;
    vector<char> ops;

    void calc() {
        int a = nums.back();
        nums.pop_back();
        int b = nums.back();
        nums.pop_back();
        char op = ops.back();
        ops.pop_back();
        switch (op) {
            case '+' : nums.push_back(b + a); break;
            case '-' : nums.push_back(b - a); break;
            case '*' : nums.push_back(b * a); break;
            case '/' : nums.push_back(b / a); break;
        }
    }

    int calculate(string s) {
        int i = 0;
        while (i < s.size()) {
            if (s[i] == ' ') {  // don't use "if (s[i++] == ' ')" !!!
                i++;
                continue;
            }
            if (s[i] >= '0' && s[i] <= '9') {
                int k = 0;
                while (i < s.size() && s[i] >= '0' && s[i] <= '9') {
                    k = 10 * k + s[i++] - '0';
                }
                nums.push_back(k);
            } else {
                if (ops.empty()) {
                    ops.push_back(s[i++]);
                } else {
                    if (s[i] == '+' || s[i] == '-') {
                        while (!ops.empty()) {
                            calc();
                        }
                        ops.push_back(s[i++]);
                    } else {
                        while (!ops.empty() && (ops.back() == '*' || ops.back() == '/')) {
                            calc();
                        }
                        ops.push_back(s[i++]);
                    }
                }
                
            }
        }
        if (nums.empty()) {
            return 0;
        } else {
            while (!ops.empty()) {
                calc();
            }
            return nums.back();
        }
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
