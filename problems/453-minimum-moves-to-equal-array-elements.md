## 453. Minimum Moves to Equal Array Elements - 最小移动次数使数组元素相等

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个长度为 <em>n</em> 的<strong>非空</strong>整数数组，找到让数组所有元素相等的最小移动次数。每次移动可以使 <em>n</em> - 1 个元素增加 1。</p>

<p><strong>示例:</strong></p>

<pre>
<strong>输入:</strong>
[1,2,3]

<strong>输出:</strong>
3

<strong>解释:</strong>
只需要3次移动（注意每次移动会增加两个元素的值）：

[1,2,3]  =&gt;  [2,3,3]  =&gt;  [3,4,3]  =&gt;  [4,4,4]
</pre>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/minimum-moves-to-equal-array-elements/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-moves-to-equal-array-elements/description/)

## 题解

每次操作，其它元素都+1，等效于一个元素相对-1

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 52  ms | N/A |

```python3
class Solution:
    def minMoves(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return sum(nums) - min(nums) * len(nums)
```
