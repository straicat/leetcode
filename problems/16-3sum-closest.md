## 16. 3Sum Closest - 最接近的三数之和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个包括&nbsp;<em>n</em> 个整数的数组&nbsp;<code>nums</code><em>&nbsp;</em>和 一个目标值&nbsp;<code>target</code>。找出&nbsp;<code>nums</code><em>&nbsp;</em>中的三个整数，使得它们的和与&nbsp;<code>target</code>&nbsp;最接近。返回这三个数的和。假定每组输入只存在唯一答案。</p>

<pre>例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.

与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).
</pre>



-----

题目标签：Array / Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/3sum-closest/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/3sum-closest/description/)

## 题解

首次AC的做法：将三元组问题转为二元组问题。先排序数组，对于数组里每个不重复数，找右侧数组的二元组距离 目标减去该数 的最小间隔，然后取最小间隔加上目标即可。不过，貌似时间复杂度比较高。。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 568  ms | N/A |

```python3
class Solution:
    def twoSum(self, nums, k):
        mspan = None
        i, j = 0, len(nums) - 1
        while i < j:
            if nums[i] + nums[j] == k:
                return 0
            else:
                span = nums[i] + nums[j] - k
                if mspan is None or abs(span) < abs(mspan):
                    mspan = span
                if nums[i] + nums[j] < k:
                    i += 1
                else:
                    j -= 1
        return mspan
                
    def threeSumClosest(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        nums.sort()
        tmp = set()
        rst = []
        for i, num in enumerate(nums):
            if num not in tmp:
                mspan = self.twoSum(nums[i+1:], target - num)
                if mspan is not None:
                    rst.append(mspan)
                tmp.add(num)
        rst.sort(key=lambda x: abs(x))
        return rst[0] + target
```
