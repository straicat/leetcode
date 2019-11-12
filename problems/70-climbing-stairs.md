## 70. Climbing Stairs - 爬楼梯

<!--If you want to use the English description, use `question.content` instead-->

<p>假设你正在爬楼梯。需要 <em>n</em>&nbsp;阶你才能到达楼顶。</p>

<p>每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？</p>

<p><strong>注意：</strong>给定 <em>n</em> 是一个正整数。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong> 2
<strong>输出：</strong> 2
<strong>解释：</strong> 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong> 3
<strong>输出：</strong> 3
<strong>解释：</strong> 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶
</pre>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/climbing-stairs/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/climbing-stairs/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | N/A |

```python3
class Solution:
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        steps = [1, 2]
        if n < 3:
            return n
        else:
            for i in range(n-2):
                if i % 2 == 0:
                    steps[0] += steps[1]
                else:
                    steps[1] += steps[0]
            if n % 2 == 0:
                return steps[1]
            else:
                return steps[0]
```
