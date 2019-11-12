## 645. Set Mismatch - 错误的集合

<!--If you want to use the English description, use `question.content` instead-->

<p>集合 <code>S</code> 包含从1到&nbsp;<code>n</code>&nbsp;的整数。不幸的是，因为数据错误，导致集合里面某一个元素复制了成了集合里面的另外一个元素的值，导致集合丢失了一个整数并且有一个元素重复。</p>

<p>给定一个数组 <code>nums</code> 代表了集合 <code>S</code> 发生错误后的结果。你的任务是首先寻找到重复出现的整数，再找到丢失的整数，将它们以数组的形式返回。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> nums = [1,2,2,4]
<strong>输出:</strong> [2,3]
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>给定数组的长度范围是&nbsp;[2, 10000]。</li>
	<li>给定的数组是无序的。</li>
</ol>



-----

题目标签：Hash Table / Math

题目链接：[LeetCode](https://leetcode.com/problems/set-mismatch/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/set-mismatch/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 60  ms | N/A |

```python3
class Solution:
    def findErrorNums(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        a = [False] * len(nums)
        res = [None, None]
        for num in nums:
            if a[num-1]:
                res[0] = num
            else:
                a[num-1] = True
        res[1] = a.index(False) + 1
        return res
```
