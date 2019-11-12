## 930. Binary Subarrays With Sum - 和相同的二元子数组

<!--If you want to use the English description, use `question.content` instead-->

<p>在由若干&nbsp;<code>0</code>&nbsp;和&nbsp;<code>1</code>&nbsp; 组成的数组&nbsp;<code>A</code>&nbsp;中，有多少个和为 <code>S</code>&nbsp;的<strong>非空</strong>子数组。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>A = [1,0,1,0,1], S = 2
<strong>输出：</strong>4
<strong>解释：</strong>
如下面黑体所示，有 4 个满足题目要求的子数组：
[<strong>1,0,1</strong>,0,1]
[<strong>1,0,1,0</strong>,1]
[1,<strong>0,1,0,1</strong>]
[1,0,<strong>1,0,1</strong>]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>A.length &lt;= 30000</code></li>
	<li><code>0 &lt;= S &lt;= A.length</code></li>
	<li><code>A[i]</code>&nbsp;为&nbsp;<code>0</code>&nbsp;或&nbsp;<code>1</code></li>
</ol>



-----

题目标签：Hash Table / Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/binary-subarrays-with-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-subarrays-with-sum/description/)

## 题解

对于子数组之和的问题，考虑使用数组的累加和，则子数组之和就是累加和数组中两个数之差或累加数组中的某个数。

对于本题，扫描累加和数组的每个元素s，看其左侧S-s的个数，每一个都可以构成符合题意的子数组；另外，如果s等于S，那么，再加1。

例如，A=[1,0,1,0,1]，S=2，其累加和数组为：[1,1,2,2,3]。

扫描累加和数组：对于1，显然不符合；对于2，结果+2（因为有两个2，且这两个2的左侧0的次数均为0）；对于3，结果+2（因为3的左侧1的次数为2）

因此，可以扫描A，计算累加和s，如果s等于S，就先将结果+1，然后将结果+累加和数组左侧S-s的个数，我们可以用dict来存储个数信息。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 120  ms | N/A |

```python3
class Solution:
    def numSubarraysWithSum(self, A, S):
        """
        :type A: List[int]
        :type S: int
        :rtype: int
        """
        prev_cnt=collections.defaultdict(int)
        res = 0
        prev_sum = 0
        for a in A:
            prev_sum += a
            if prev_sum == S:
                res += 1
            res += prev_cnt[prev_sum - S]
            prev_cnt[prev_sum] += 1
        return res
```
