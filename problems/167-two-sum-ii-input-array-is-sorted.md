## 167. Two Sum II - Input array is sorted - 两数之和 II - 输入有序数组

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个已按照<strong><em>升序排列</em>&nbsp;</strong>的有序数组，找到两个数使得它们相加之和等于目标数。</p>

<p>函数应该返回这两个下标值<em> </em>index1 和 index2，其中 index1&nbsp;必须小于&nbsp;index2<em>。</em></p>

<p><strong>说明:</strong></p>

<ul>
	<li>返回的下标值（index1 和 index2）不是从零开始的。</li>
	<li>你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。</li>
</ul>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> numbers = [2, 7, 11, 15], target = 9
<strong>输出:</strong> [1,2]
<strong>解释:</strong> 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。</pre>



-----

题目标签：Array / Two Pointers / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | N/A |

```python3
class Solution:
    def twoSum(self, numbers, target):
        """
        :type numbers: List[int]
        :type target: int
        :rtype: List[int]
        """
        sn = sorted(list(set(numbers)))
        for n in sn:
            if target - n in sn:
                a, b = n, target - n
                break
        i = numbers.index(a)+1
        j = numbers.index(b)+1
        if i == j:
            j = i + 1
        return i, j
```
