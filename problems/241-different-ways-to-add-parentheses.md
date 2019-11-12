## 241. Different Ways to Add Parentheses - 为运算表达式设计优先级

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个含有数字和运算符的字符串，为表达式添加括号，改变其运算优先级以求出不同的结果。你需要给出所有可能的组合的结果。有效的运算符号包含 <code>+</code>,&nbsp;<code>-</code>&nbsp;以及&nbsp;<code>*</code>&nbsp;。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> <code>&quot;2-1-1&quot;</code>
<strong>输出:</strong> <code>[0, 2]</code>
<strong>解释: </strong>
((2-1)-1) = 0 
(2-(1-1)) = 2</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入: </strong><code>&quot;2*3-4*5&quot;</code>
<strong>输出:</strong> <code>[-34, -14, -10, -10, 10]</code>
<strong>解释: 
</strong>(2*(3-(4*5))) = -34 
((2*3)-(4*5)) = -14 
((2*(3-4))*5) = -10 
(2*((3-4)*5)) = -10 
(((2*3)-4)*5) = 10</pre>



-----

题目标签：Divide and Conquer

题目链接：[LeetCode](https://leetcode.com/problems/different-ways-to-add-parentheses/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/different-ways-to-add-parentheses/description/)

## 题解

分治法

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 15.6 MB |

```cpp
class Solution {
public:
    vector<int> diffWaysToCompute(string input) {
        static unordered_map<string, vector<int>> cache;
        bool isNum = true;
        vector<int> res;
        for (int i = 0; i < input.length(); i++) {
            if (!isdigit(input[i])) {
                isNum = false;
                vector<int> a = diffWaysToCompute(input.substr(0, i));
                vector<int> b = diffWaysToCompute(input.substr(i + 1));
                for (int ai : a) {
                    for (int bi : b) {
                        switch(input[i]) {
                            case '+': res.push_back(ai + bi); break;
                            case '-': res.push_back(ai - bi); break;
                            case '*': res.push_back(ai * bi); break;
                            case '/': res.push_back(ai / bi); break;
                        }
                    }
                }
            }
        }
        if (isNum) {
            res.push_back(stoi(input));
        } else {
        }
        return cache[input] = res;
    }
};
```
