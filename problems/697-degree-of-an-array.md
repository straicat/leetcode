## 697. Degree of an Array - 数组的度

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非空且只包含非负数的整数数组&nbsp;<code>nums</code>, 数组的度的定义是指数组里任一元素出现频数的最大值。</p>

<p>你的任务是找到与&nbsp;<code>nums</code>&nbsp;拥有相同大小的度的最短连续子数组，返回其长度。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1, 2, 2, 3, 1]
<strong>输出:</strong> 2
<strong>解释:</strong> 
输入数组的度是2，因为元素1和2的出现频数最大，均为2.
连续子数组里面拥有相同度的有如下所示:
[1, 2, 2, 3, 1], [1, 2, 2, 3], [2, 2, 3, 1], [1, 2, 2], [2, 2, 3], [2, 2]
最短连续子数组[2, 2]的长度为2，所以返回2.
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> [1,2,2,3,1,4,2]
<strong>输出:</strong> 6
</pre>

<p><strong>注意:</strong></p>

<ul>
	<li><code>nums.length</code>&nbsp;在1到50,000区间范围内。</li>
	<li><code>nums[i]</code>&nbsp;是一个在0到49,999范围内的整数。</li>
</ul>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/degree-of-an-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/degree-of-an-array/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 1208  ms | N/A |

```python3
class Solution:
    def findShortestSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        res = len(nums)
        cnt = sorted(collections.Counter(nums).items(), key=lambda x: x[1], reverse=True)
        ns = [i[0] for i in filter(lambda x: x[1] == cnt[0][1], cnt)]
        for n in ns:
            res = min(res, len(nums)-1-nums[::-1].index(n) - nums.index(n) + 1)
        return res
```
