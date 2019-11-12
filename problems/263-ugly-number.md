## 263. Ugly Number - 丑数

<!--If you want to use the English description, use `question.content` instead-->

<p>编写一个程序判断给定的数是否为丑数。</p>

<p>丑数就是只包含质因数&nbsp;<code>2, 3, 5</code>&nbsp;的<strong>正整数</strong>。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 6
<strong>输出:</strong> true
<strong>解释: </strong>6 = 2 &times;&nbsp;3</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 8
<strong>输出:</strong> true
<strong>解释: </strong>8 = 2 &times; 2 &times;&nbsp;2
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入:</strong> 14
<strong>输出:</strong> false 
<strong>解释: </strong><code>14</code> 不是丑数，因为它包含了另外一个质因数&nbsp;<code>7</code>。</pre>

<p><strong>说明：</strong></p>

<ol>
	<li><code>1</code>&nbsp;是丑数。</li>
	<li>输入不会超过 32 位有符号整数的范围:&nbsp;[&minus;2<sup>31</sup>,&nbsp; 2<sup>31&nbsp;</sup>&minus; 1]。</li>
</ol>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/ugly-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ugly-number/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 8 MB |

```cpp
int factors[] = {2, 3, 5};

class Solution {
public:
    bool isUgly(int num) {
        if (num <= 0) return false;
        if (num < 2) return true;
        for (int n : factors) {
            if (num % n == 0) {
                return isUgly(num / n);
            }
        }
        return false;
    }
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 76  ms | N/A |

```python3
class Solution:
    def isUgly(self, num):
        """
        :type num: int
        :rtype: bool
        """
        for pf in (2, 3, 5):
            while num != 0 and not num % pf:
                num //= pf
        return num == 1
```
