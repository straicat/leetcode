## 442. Find All Duplicates in an Array - 数组中重复的数据

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组 a，其中1 &le; a[i] &le; <em>n</em> （<em>n</em>为数组长度）, 其中有些元素出现<strong>两次</strong>而其他元素出现<strong>一次</strong>。</p>

<p>找到所有出现<strong>两次</strong>的元素。</p>

<p>你可以不用到任何额外空间并在O(<em>n</em>)时间复杂度内解决这个问题吗？</p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入:</strong>
[4,3,2,7,8,2,3,1]

<strong>输出:</strong>
[2,3]
</pre>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/find-all-duplicates-in-an-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-all-duplicates-in-an-array/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 200  ms | N/A |

```python3
class Solution:
    def findDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        tmp = [False] * len(nums)
        res = []
        for num in nums:
            if tmp[num-1]:
                res.append(num)
            else:
                tmp[num-1] = True
        return res
```
