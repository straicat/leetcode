## 303. Range Sum Query - Immutable - 区域和检索 - 数组不可变

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组 &nbsp;<em>nums</em>，求出数组从索引&nbsp;<em>i&nbsp;</em>到&nbsp;<em>j&nbsp;&nbsp;</em>(<em>i</em>&nbsp;&le;&nbsp;<em>j</em>) 范围内元素的总和，包含&nbsp;<em>i,&nbsp; j&nbsp;</em>两点。</p>

<p><strong>示例：</strong></p>

<pre>给定 nums = [-2, 0, 3, -5, 2, -1]，求和函数为 sumRange()

sumRange(0, 2) -&gt; 1
sumRange(2, 5) -&gt; -1
sumRange(0, 5) -&gt; -3</pre>

<p><strong>说明:</strong></p>

<ol>
	<li>你可以假设数组不可变。</li>
	<li>会多次调用&nbsp;<em>sumRange</em>&nbsp;方法。</li>
</ol>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/range-sum-query-immutable/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/range-sum-query-immutable/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 56  ms | N/A |

```python3
class NumArray:

    def __init__(self, nums):
        """
        :type nums: List[int]
        """
        self.sums = [0]
        for i, n in enumerate(nums):
            self.sums.append(self.sums[i] + n)

    def sumRange(self, i, j):
        """
        :type i: int
        :type j: int
        :rtype: int
        """
        return self.sums[j+1] - self.sums[i]


# Your NumArray object will be instantiated and called as such:
# obj = NumArray(nums)
# param_1 = obj.sumRange(i,j)
```
