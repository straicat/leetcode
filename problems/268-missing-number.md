## 268. Missing Number - 缺失数字

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个包含 <code>0, 1, 2, ..., n</code>&nbsp;中&nbsp;<em>n</em>&nbsp;个数的序列，找出 0 .. <em>n</em>&nbsp;中没有出现在序列中的那个数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [3,0,1]
<strong>输出:</strong> 2
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [9,6,4,2,3,5,7,0,1]
<strong>输出:</strong> 8
</pre>

<p><strong>说明:</strong><br>
你的算法应具有线性时间复杂度。你能否仅使用额外常数空间来实现?</p>



-----

题目标签：Bit Manipulation / Array / Math

题目链接：[LeetCode](https://leetcode.com/problems/missing-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/missing-number/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 48  ms | N/A |

```python3
class Solution:
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        tmp = [-1] * (len(nums) + 1)
        for n in nums:
            tmp[n] = 1
        return tmp.index(-1)
```
