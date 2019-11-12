## 4. Median of Two Sorted Arrays - 寻找两个有序数组的中位数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个大小为 m 和 n 的有序数组&nbsp;<code>nums1</code> 和&nbsp;<code>nums2</code>。</p>

<p>请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为&nbsp;O(log(m + n))。</p>

<p>你可以假设&nbsp;<code>nums1</code>&nbsp;和&nbsp;<code>nums2</code>&nbsp;不会同时为空。</p>

<p><strong>示例 1:</strong></p>

<pre>nums1 = [1, 3]
nums2 = [2]

则中位数是 2.0
</pre>

<p><strong>示例 2:</strong></p>

<pre>nums1 = [1, 2]
nums2 = [3, 4]

则中位数是 (2 + 3)/2 = 2.5
</pre>



-----

题目标签：Array / Binary Search / Divide and Conquer

题目链接：[LeetCode](https://leetcode.com/problems/median-of-two-sorted-arrays/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 92  ms | N/A |

```python3
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        nums = sorted(nums1 + nums2)
        if len(nums) % 2:
            return nums[len(nums) // 2]
        else:
            return (nums[len(nums) // 2] + nums[len(nums) // 2 - 1]) / 2
```
