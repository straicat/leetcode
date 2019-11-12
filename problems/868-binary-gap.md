## 868. Binary Gap - 二进制间距

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个正整数&nbsp;<code>N</code>，找到并返回 <code>N</code>&nbsp;的二进制表示中两个连续的 1 之间的最长距离。&nbsp;</p>

<p>如果没有两个连续的 1，返回 <code>0</code> 。</p>

<p>&nbsp;</p>

<ul>
</ul>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>22
<strong>输出：</strong>2
<strong>解释：</strong>
22 的二进制是 0b10110 。
在 22 的二进制表示中，有三个 1，组成两对连续的 1 。
第一对连续的 1 中，两个 1 之间的距离为 2 。
第二对连续的 1 中，两个 1 之间的距离为 1 。
答案取两个距离之中最大的，也就是 2 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>5
<strong>输出：</strong>2
<strong>解释：</strong>
5 的二进制是 0b101 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>6
<strong>输出：</strong>1
<strong>解释：</strong>
6 的二进制是 0b110 。
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>8
<strong>输出：</strong>0
<strong>解释：</strong>
8 的二进制是 0b1000 。
在 8 的二进制表示中没有连续的 1，所以返回 0 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= N &lt;= 10^9</code></li>
</ul>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/binary-gap/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-gap/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 88  ms | N/A |

```python3
class Solution:
    def binaryGap(self, N):
        """
        :type N: int
        :rtype: int
        """
        res = 0
        pre = -1
        for i, n in enumerate(bin(N)[2:]):
            if n == '1':
                if pre != -1:
                    res = max(res, i-pre)
                pre = i
        return res
```
