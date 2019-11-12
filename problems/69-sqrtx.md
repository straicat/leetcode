## 69. Sqrt(x) - x 的平方根

<!--If you want to use the English description, use `question.content` instead-->

<p>实现&nbsp;<code>int sqrt(int x)</code>&nbsp;函数。</p>

<p>计算并返回&nbsp;<em>x</em>&nbsp;的平方根，其中&nbsp;<em>x </em>是非负整数。</p>

<p>由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 4
<strong>输出:</strong> 2
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 8
<strong>输出:</strong> 2
<strong>说明:</strong> 8 的平方根是 2.82842..., 
&nbsp;    由于返回类型是整数，小数部分将被舍去。
</pre>



-----

题目标签：Math / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/sqrtx/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sqrtx/description/)

## 题解

牛顿法求f(x)=0的根：

x = x - f(x)/f'(x)

对于sqrt(n)，也就是求f(x)=x^2-n=0的根。



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 1  ms | 32.2 MB |

```java
class Solution {
    public int mySqrt(int x) {
        int l = 0;
        int r = x;
        while (l < r) {
            int mid = (int)(l + r + 1l) >> 1;
            if (mid <= x / mid) l = mid;
            else r = mid - 1;
        }
        return l;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 8.3 MB |

```cpp
class Solution {
public:
    int mySqrt(int x) {
        // sqrt(x) = y  ->  x = y^2
        int left = 0;
        int right = x;
        while (left < right) {
            int mid = left + (right - left + 1ll) / 2;
            if (mid > x / mid) right = mid - 1;
            else left = mid;
        }
        return left;
    }
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 56  ms | N/A |

```python3
class Solution:
    def mySqrt(self, x):
        """
        :type x: int
        :rtype: int
        """
        pre = 1
        while True:
            res = 0.5 * (pre + x / pre)
            if abs(res - pre) < 1:
                break
            pre = res
        return int(res)
```
