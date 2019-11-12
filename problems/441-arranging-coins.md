## 441. Arranging Coins - 排列硬币

<!--If you want to use the English description, use `question.content` instead-->

<p>你总共有&nbsp;<em>n&nbsp;</em>枚硬币，你需要将它们摆成一个阶梯形状，第&nbsp;<em>k&nbsp;</em>行就必须正好有&nbsp;<em>k&nbsp;</em>枚硬币。</p>

<p>给定一个数字&nbsp;<em>n</em>，找出可形成完整阶梯行的总行数。</p>

<p><em>n&nbsp;</em>是一个非负整数，并且在32位有符号整型的范围内。</p>

<p><strong>示例 1:</strong></p>

<pre>
n = 5

硬币可排列成以下几行:
&curren;
&curren; &curren;
&curren; &curren;

因为第三行不完整，所以返回2.
</pre>

<p><strong>示例 2:</strong></p>

<pre>
n = 8

硬币可排列成以下几行:
&curren;
&curren; &curren;
&curren; &curren; &curren;
&curren; &curren;

因为第四行不完整，所以返回3.
</pre>



-----

题目标签：Math / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/arranging-coins/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/arranging-coins/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 60  ms | N/A |

```python3
class Solution:
    def arrangeCoins(self, n):
        """
        :type n: int
        :rtype: int
        """
        return int((math.sqrt(8*n+1)-1)/2)
```
