## 40. Combination Sum II - 组合总和 II

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个数组&nbsp;<code>candidates</code>&nbsp;和一个目标数&nbsp;<code>target</code>&nbsp;，找出&nbsp;<code>candidates</code>&nbsp;中所有可以使数字和为&nbsp;<code>target</code>&nbsp;的组合。</p>

<p><code>candidates</code>&nbsp;中的每个数字在每个组合中只能使用一次。</p>

<p><strong>说明：</strong></p>

<ul>
	<li>所有数字（包括目标数）都是正整数。</li>
	<li>解集不能包含重复的组合。&nbsp;</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> candidates =&nbsp;<code>[10,1,2,7,6,1,5]</code>, target =&nbsp;<code>8</code>,
<strong>所求解集为:</strong>
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> candidates =&nbsp;[2,5,2,1,2], target =&nbsp;5,
<strong>所求解集为:</strong>
[
&nbsp; [1,2,2],
&nbsp; [5]
]</pre>



-----

题目标签：Array / Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/combination-sum-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combination-sum-ii/description/)

## 题解

要列出所有组合，显然可以暴力，因此可以用递归，主要难点在于如何保证不重复。

首先规定取了一个元素后，只能取其右侧的元素。但是，重复元素怎么处理呢？这里可以先进行排序，每次通过检查最后一个结果来判别重复。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 104  ms | N/A |

```python3
class Solution:
    def combinationSum2(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        candidates.sort()
        res = []
        for i, num in enumerate(candidates):
            if num == target and (not res or res[-1][0] != num):
                res.append([num])
            elif num < target and (not res or res[-1][0] != num):
                for r in self.combinationSum2(candidates[i+1:], target-num):
                    res.append([num, *r])
        return res
```
