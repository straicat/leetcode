## 238. Product of Array Except Self - 除自身以外数组的乘积

<!--If you want to use the English description, use `question.content` instead-->

<p>给定长度为&nbsp;<em>n</em>&nbsp;的整数数组&nbsp;<code>nums</code>，其中&nbsp;<em>n</em> &gt; 1，返回输出数组&nbsp;<code>output</code>&nbsp;，其中 <code>output[i]</code>&nbsp;等于&nbsp;<code>nums</code>&nbsp;中除&nbsp;<code>nums[i]</code>&nbsp;之外其余各元素的乘积。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> <code>[1,2,3,4]</code>
<strong>输出:</strong> <code>[24,12,8,6]</code></pre>

<p><strong>说明: </strong>请<strong>不要使用除法，</strong>且在&nbsp;O(<em>n</em>) 时间复杂度内完成此题。</p>

<p><strong>进阶：</strong><br>
你可以在常数空间复杂度内完成这个题目吗？（ 出于对空间复杂度分析的目的，输出数组<strong>不被视为</strong>额外空间。）</p>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/product-of-array-except-self/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/product-of-array-except-self/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 148  ms | N/A |

```python3
class Solution:
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        left = [1] * len(nums)
        right = [1] * len(nums)
        res = [1] * len(nums)
        for i in range(1, len(nums)):
            left[i] = left[i-1] * nums[i-1]
            right[len(nums) - 1 - i] = right[len(nums) - i] * nums[len(nums) - i]
        for i in range(len(nums)):
            res[i] = left[i] * right[i]
        return res
```
