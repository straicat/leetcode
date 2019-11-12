## 581. Shortest Unsorted Continuous Subarray - 最短无序连续子数组

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组，你需要寻找一个<strong>连续的子数组</strong>，如果对这个子数组进行升序排序，那么整个数组都会变为升序排序。</p>

<p>你找到的子数组应是<strong>最短</strong>的，请输出它的长度。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [2, 6, 4, 8, 10, 9, 15]
<strong>输出:</strong> 5
<strong>解释:</strong> 你只需要对 [6, 4, 8, 10, 9] 进行升序排序，那么整个表都会变为升序排序。
</pre>

<p><strong>说明 :</strong></p>

<ol>
	<li>输入的数组长度范围在&nbsp;[1, 10,000]。</li>
	<li>输入的数组可能包含<strong>重复</strong>元素&nbsp;，所以<strong>升序</strong>的意思是<strong>&lt;=。</strong></li>
</ol>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shortest-unsorted-continuous-subarray/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 124  ms | N/A |

```python3
class Solution:
    def findUnsortedSubarray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        '''
        排序前：[2, 6, 4, 8, 10,  9, 15]
        排序后：[2, 4, 6, 8,  9, 10, 15]
        思路：排序前后首尾比对
        '''
        snums = sorted(nums)
        cnt = 0
        for i in range(len(nums)):
            if nums[i] == snums[i]:
                cnt += 1
            else:
                break
        for j in range(len(nums)-1, i, -1):
            if nums[j] == snums[j]:
                cnt += 1
            else:
                break
        return len(nums) - cnt
```
