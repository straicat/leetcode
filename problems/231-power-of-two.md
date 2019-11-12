## 231. Power of Two - 2的幂

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数，编写一个函数来判断它是否是 2 的幂次方。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> 1
<strong>输出:</strong> true
<strong>解释: </strong>2<sup>0</sup>&nbsp;= 1</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 16
<strong>输出:</strong> true
<strong>解释: </strong>2<sup>4</sup>&nbsp;= 16</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> 218
<strong>输出:</strong> false</pre>



-----

题目标签：Bit Manipulation / Math

题目链接：[LeetCode](https://leetcode.com/problems/power-of-two/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/power-of-two/description/)

## 题解

利用位运算来判断是否为2的幂。2的幂的二进制特点是：最高位为1，其余全为0;而2的幂-1的二进制特点是：所有位都为1。因此，进行按位与，结果是0。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | N/A |

```cpp
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if(n > 0)
            return !(n & (n-1));
        else
            return false;
    }
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 56  ms | N/A |

```python3
class Solution:
    def isPowerOfTwo(self, n):
        """
        :type n: int
        :rtype: bool
        """
        return not (n & (n-1)) if n > 0 else False
```
