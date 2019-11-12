## 448. Find All Numbers Disappeared in an Array - 找到所有数组中消失的数字

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个范围在&nbsp; 1 &le; a[i] &le; <em>n</em> (&nbsp;<em>n</em> = 数组大小 ) 的 整型数组，数组中的元素一些出现了两次，另一些只出现一次。</p>

<p>找到所有在 [1, <em>n</em>] 范围之间没有出现在数组中的数字。</p>

<p>您能在不使用额外空间且时间复杂度为<em>O(n)</em>的情况下完成这个任务吗? 你可以假定返回的数组不算在额外空间内。</p>

<p><strong>示例:</strong></p>

<pre>
<strong>输入:</strong>
[4,3,2,7,8,2,3,1]

<strong>输出:</strong>
[5,6]
</pre>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-all-numbers-disappeared-in-an-array/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 208  ms | N/A |

```python3
class Solution:
    def findDisappearedNumbers(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        return sorted(list(set(x for x in range(1, len(nums)+1)) - set(nums)))
```
