## 46. Permutations - 全排列

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个<strong>没有重复</strong>数字的序列，返回其所有可能的全排列。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,2,3]
<strong>输出:</strong>
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]</pre>



-----

题目标签：Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/permutations/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/permutations/description/)

## 题解

用Python的话，可以直接用内建的`itertools`模块，一行搞定，宛如开挂。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 76  ms | N/A |

```python3
class Solution:
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        return list(itertools.permutations(nums))
```
