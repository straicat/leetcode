## 923. 3Sum With Multiplicity - 三数之和的多种可能

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组&nbsp;<code>A</code>，以及一个整数&nbsp;<code>target</code>&nbsp;作为目标值，返回满足 <code>i &lt; j &lt; k</code> 且&nbsp;<code>A[i] + A[j] + A[k] == target</code>&nbsp;的元组&nbsp;<code>i, j, k</code>&nbsp;的数量。</p>

<p>由于结果会非常大，请返回 <code>结果除以 10^9 + 7 的余数</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>A = [1,1,2,2,3,3,4,4,5,5], target = 8
<strong>输出：</strong>20
<strong>解释：</strong>
按值枚举（A[i]，A[j]，A[k]）：
(1, 2, 5) 出现 8 次；
(1, 3, 4) 出现 8 次；
(2, 2, 4) 出现 2 次；
(2, 3, 3) 出现 2 次。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>A = [1,1,2,2,2,2], target = 5
<strong>输出：</strong>12
<strong>解释：</strong>
A[i] = 1，A[j] = A[k] = 2 出现 12 次：
我们从 [1,1] 中选择一个 1，有 2 种情况，
从 [2,2,2,2] 中选出两个 2，有 6 种情况。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>3 &lt;= A.length &lt;= 3000</code></li>
	<li><code>0 &lt;= A[i] &lt;= 100</code></li>
	<li><code>0 &lt;= target &lt;= 300</code></li>
</ol>



-----

题目标签：Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/3sum-with-multiplicity/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/3sum-with-multiplicity/description/)

## 题解

该题是3Sum问题的变形。首先找不重复的三元组，然后对每个三元组看其有多少种组合方式，最后把种数累加起来即可。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 372  ms | N/A |

```python3
class Solution:
    def twoSum(self, nums, target):
        res = []
        i, j = 0, len(nums) - 1
        while i < j:
            if nums[i] + nums[j] == target:
                if not res or res[-1][0] != nums[i]:
                    res.append([nums[i], nums[j]])
                i += 1
                j -= 1
            elif nums[i] + nums[j] > target:
                j -= 1
            else:
                i += 1
        return res

    def threeSumMulti(self, A, target):
        """
        :type A: List[int]
        :type target: int
        :rtype: int
        """
        rst = []
        A.sort()
        vt = set()
        for i, num in enumerate(A):
            if num not in vt:
                for twosum in self.twoSum(A[i+1:], target - num):
                    rst.append([num, *twosum])
                vt.add(num)
        cnt = collections.Counter(A)
        res = 0
        for muti in rst:
            t = 1
            for num in set(muti):
                if muti.count(num) == 1:
                    t *= cnt[num]
                elif muti.count(num) == 2:
                    t *= cnt[num] * (cnt[num] - 1) // 2
                else:
                    t *= cnt[num] * (cnt[num] - 1) * (cnt[num] - 2) // 6
            res += t
        return res % (10**9 + 7)
```
