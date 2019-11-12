## 485. Max Consecutive Ones - 最大连续1的个数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二进制数组， 计算其中最大连续1的个数。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1,1,0,1,1,1]
<strong>输出:</strong> 3
<strong>解释:</strong> 开头的两位和最后的三位都是连续1，所以最大连续1的个数是 3.
</pre>

<p><strong>注意：</strong></p>

<ul>
	<li>输入的数组只包含&nbsp;<code>0</code> 和<code>1</code>。</li>
	<li>输入数组的长度是正整数，且不超过 10,000。</li>
</ul>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/max-consecutive-ones/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/max-consecutive-ones/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 168  ms | N/A |

```python3
class Solution:
    def findMaxConsecutiveOnes(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return len(sorted(''.join(map(str, nums)).split('0'), key=lambda x: len(x))[-1])
```
