## 172. Factorial Trailing Zeroes - 阶乘后的零

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数 <em>n</em>，返回 <em>n</em>! 结果尾数中零的数量。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 3
<strong>输出:</strong> 0
<strong>解释:</strong>&nbsp;3! = 6, 尾数中没有零。</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> 5
<strong>输出:</strong> 1
<strong>解释:</strong>&nbsp;5! = 120, 尾数中有 1 个零.</pre>

<p><strong>说明: </strong>你算法的时间复杂度应为&nbsp;<em>O</em>(log&nbsp;<em>n</em>)<em>&nbsp;</em>。</p>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/factorial-trailing-zeroes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/factorial-trailing-zeroes/description/)

## 题解

注意int的边界

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | N/A |

```cpp
class Solution {
public:
    int trailingZeroes(int n) {
        int res = 0;
        for(long p = 5; n / p > 0; p *= 5)
            res += n / p;
        return res;
    }
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 44  ms | N/A |

```python3
class Solution:
    def trailingZeroes(self, n):
        """
        :type n: int
        :rtype: int
        """
        p = 5
        res = 0
        while p <= n:
            res += n // p
            p *= 5
        return res
```
