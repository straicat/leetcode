## 674. Longest Continuous Increasing Subsequence - 最长连续递增序列

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个未经排序的整数数组，找到最长且<strong>连续</strong>的的递增序列。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1,3,5,4,7]
<strong>输出:</strong> 3
<strong>解释:</strong> 最长连续递增序列是 [1,3,5], 长度为3。
尽管 [1,3,5,7] 也是升序的子序列, 但它不是连续的，因为5和7在原数组里被4隔开。 
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> [2,2,2,2,2]
<strong>输出:</strong> 1
<strong>解释:</strong> 最长连续递增序列是 [2], 长度为1。
</pre>

<p><strong>注意：</strong>数组长度不会超过10000。</p>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/longest-continuous-increasing-subsequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-continuous-increasing-subsequence/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 48  ms | N/A |

```python3
class Solution:
    def findLengthOfLCIS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        res = 1
        tmp = 1
        if len(nums) < 2:
            return len(nums)
        for i in range(1, len(nums)):
            if nums[i] > nums[i-1]:
                tmp += 1
            else:
                res = max(res, tmp)
                tmp = 1
        res = max(res, tmp)
        return res
```
