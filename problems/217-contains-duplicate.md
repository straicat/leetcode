## 217. Contains Duplicate - 存在重复元素

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组，判断是否存在重复元素。</p>

<p>如果任何值在数组中出现至少两次，函数返回 true。如果数组中每个元素都不相同，则返回 false。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,2,3,1]
<strong>输出:</strong> true</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>[1,2,3,4]
<strong>输出:</strong> false</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入: </strong>[1,1,1,3,3,4,3,2,4,2]
<strong>输出:</strong> true</pre>



-----

题目标签：Array / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/contains-duplicate/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/contains-duplicate/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 44  ms | N/A |

```python3
class Solution:
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        return len(set(nums)) < len(nums)
```
