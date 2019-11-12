## 306. Additive Number - 累加数

<!--If you want to use the English description, use `question.content` instead-->

<p>累加数是一个字符串，组成它的数字可以形成累加序列。</p>

<p>一个有效的累加序列必须<strong>至少</strong>包含 3 个数。除了最开始的两个数以外，字符串中的其他数都等于它之前两个数相加的和。</p>

<p>给定一个只包含数字&nbsp;<code>&#39;0&#39;-&#39;9&#39;</code>&nbsp;的字符串，编写一个算法来判断给定输入是否是累加数。</p>

<p><strong>说明:&nbsp;</strong>累加序列里的数不会以 0 开头，所以不会出现&nbsp;<code>1, 2, 03</code> 或者&nbsp;<code>1, 02, 3</code>&nbsp;的情况。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <code>&quot;112358&quot;</code>
<strong>输出:</strong> true 
<strong>解释: </strong>累加序列为: <code>1, 1, 2, 3, 5, 8 </code>。1 + 1 = 2, 1 + 2 = 3, 2 + 3 = 5, 3 + 5 = 8
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> <code>&quot;199100199&quot;</code>
<strong>输出:</strong> true 
<strong>解释: </strong>累加序列为: <code>1, 99, 100, 199。</code>1 + 99 = 100, 99 + 100 = 199</pre>

<p><strong>进阶:</strong><br>
你如何处理一个溢出的过大的整数输入?</p>



-----

题目标签：Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/additive-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/additive-number/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 847.9 KB |

```cpp
// refer: https://www.bilibili.com/video/av17731909/
class Solution {
public:
    bool isValid(string& num, int pos, long long first, long long second) {
        // valid until end, result is true
        if (pos == num.size()) {
            return true;
        }
        long long third = first + second;
        string thirdS = to_string(third);
        int m = thirdS.size();
        if (num.substr(pos, m) == thirdS) {
            return isValid(num, pos + m, second, third);
        } else {
            return false;
        }
    }

    bool isAdditiveNumber(string num) {
        if (num.size() < 3) {
            return false;
        }
        // i: length of first number
        for (int i = 1; i<=num.size() / 2; ++i) {
            if (i > 1 && num[0] == '0') {
                return false;
            }
            long long first = stoll(num.substr(0, i));
            // j: length of second number
            for (int j = 1; num.size() - i - j >= max(i, j); ++j) {
                if (j > 1 && num[i] == '0') {
                    break;
                }
                long long second = stoll(num.substr(i, j));
                if (isValid(num, i + j, first, second)) {
                    return true;
                }
            }
        }
        return false;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
