## 747. Largest Number At Least Twice of Others - 至少是其他数字两倍的最大数

<!--If you want to use the English description, use `question.content` instead-->

<p>在一个给定的数组<code>nums</code>中，总是存在一个最大元素 。</p>

<p>查找数组中的最大元素是否至少是数组中每个其他数字的两倍。</p>

<p>如果是，则返回最大元素的索引，否则返回-1。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> nums = [3, 6, 1, 0]
<strong>输出:</strong> 1
<strong>解释:</strong> 6是最大的整数, 对于数组中的其他整数,
6大于数组中其他元素的两倍。6的索引是1, 所以我们返回1.
</pre>

<p>&nbsp;</p>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> nums = [1, 2, 3, 4]
<strong>输出:</strong> -1
<strong>解释:</strong> 4没有超过3的两倍大, 所以我们返回 -1.
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ol>
	<li><code>nums</code>&nbsp;的长度范围在<code>[1, 50]</code>.</li>
	<li>每个&nbsp;<code>nums[i]</code>&nbsp;的整数范围在&nbsp;<code>[0, 100]</code>.</li>
</ol>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/largest-number-at-least-twice-of-others/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-number-at-least-twice-of-others/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 52  ms | N/A |

```python3
class Solution:
    def dominantIndex(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        a = sorted(list(set(nums)))[-2:]
        if len(a) == 1:
            return nums.index(a[0])
        elif a[0] * 2 <= a[1]:
            return nums.index(a[1])
        return -1
```
