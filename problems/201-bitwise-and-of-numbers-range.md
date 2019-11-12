## 201. Bitwise AND of Numbers Range - 数字范围按位与

<!--If you want to use the English description, use `question.content` instead-->

<p>给定范围 [m, n]，其中 0 &lt;= m &lt;= n &lt;= 2147483647，返回此范围内所有数字的按位与（包含 m, n 两端点）。</p>

<p><strong>示例 1:&nbsp;</strong></p>

<pre><strong>输入:</strong> [5,7]
<strong>输出:</strong> 4</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [0,1]
<strong>输出:</strong> 0</pre>



-----

题目标签：Bit Manipulation

题目链接：[LeetCode](https://leetcode.com/problems/bitwise-and-of-numbers-range/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/bitwise-and-of-numbers-range/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 4  ms | 34.1 MB |

```java
class Solution {
    public int rangeBitwiseAnd(int m, int n) {
        // n & (n - 1) 可以把最右的1变为0
        while (n > m) {
            n &= (n - 1);
        }
        return n;
    }
}
```
