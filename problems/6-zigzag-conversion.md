## 6. ZigZag Conversion - Z 字形变换

<!--If you want to use the English description, use `question.content` instead-->

<p>将一个给定字符串根据给定的行数，以从上往下、从左到右进行&nbsp;Z 字形排列。</p>

<p>比如输入字符串为 <code>&quot;LEETCODEISHIRING&quot;</code>&nbsp;行数为 3 时，排列如下：</p>

<pre>L   C   I   R
E T O E S I I G
E   D   H   N
</pre>

<p>之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如：<code>&quot;LCIRETOESIIGEDHN&quot;</code>。</p>

<p>请你实现这个将字符串进行指定行数变换的函数：</p>

<pre>string convert(string s, int numRows);</pre>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> s = &quot;LEETCODEISHIRING&quot;, numRows = 3
<strong>输出:</strong> &quot;LCIRETOESIIGEDHN&quot;
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> s = &quot;LEETCODEISHIRING&quot;, numRows =&nbsp;4
<strong>输出:</strong>&nbsp;&quot;LDREOEIIECIHNTSG&quot;
<strong>解释:</strong>

L     D     R
E   O E   I I
E C   I H   N
T     S     G</pre>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/zigzag-conversion/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/zigzag-conversion/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 96  ms | 11.4 MB |

```cpp
class Solution {
public:
    string convert(string s, int numRows) {
        stringstream vss[numRows];
        auto it = s.begin();
        while (it != s.end()) {
            for (int i=0; i<numRows && it != s.end(); ++i) {
                vss[i] << *it++;
            }
            for (int i=numRows-2; i>0 && it != s.end(); --i) {
                vss[i] << *it++;
            }
        }
        for (int i=1; i<numRows; ++i) {
            vss[0] << vss[i].str();
        }
        return vss[0].str();
    }
};
```
