## 371. Sum of Two Integers - 两整数之和

<!--If you want to use the English description, use `question.content` instead-->

<p><strong>不使用</strong>运算符&nbsp;<code>+</code> 和&nbsp;<code>-</code>&nbsp;​​​​​​​，计算两整数&nbsp;​​​​​​​<code>a</code>&nbsp;、<code>b</code>&nbsp;​​​​​​​之和。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>a = 1, b = 2
<strong>输出: </strong>3
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>a = -2, b = 3
<strong>输出: </strong>1</pre>



-----

题目标签：Bit Manipulation

题目链接：[LeetCode](https://leetcode.com/problems/sum-of-two-integers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sum-of-two-integers/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 835.6 KB |

```cpp
class Solution {
public:
    int getSum(int a, int b) {
        if (b == 0) {
            return a;
        } else {
            return getSum(a ^ b, (a & b) << 1);
        }
    }
};
```
