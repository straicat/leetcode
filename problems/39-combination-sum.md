## 39. Combination Sum - 组合总和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个<strong>无重复元素</strong>的数组&nbsp;<code>candidates</code>&nbsp;和一个目标数&nbsp;<code>target</code>&nbsp;，找出&nbsp;<code>candidates</code>&nbsp;中所有可以使数字和为&nbsp;<code>target</code>&nbsp;的组合。</p>

<p><code>candidates</code>&nbsp;中的数字可以无限制重复被选取。</p>

<p><strong>说明：</strong></p>

<ul>
	<li>所有数字（包括&nbsp;<code>target</code>）都是正整数。</li>
	<li>解集不能包含重复的组合。&nbsp;</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> candidates = <code>[2,3,6,7], </code>target = <code>7</code>,
<strong>所求解集为:</strong>
[
  [7],
  [2,2,3]
]
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> candidates = [2,3,5]<code>, </code>target = 8,
<strong>所求解集为:</strong>
[
&nbsp; [2,2,2,2],
&nbsp; [2,3,3],
&nbsp; [3,5]
]</pre>



-----

题目标签：Array / Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/combination-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combination-sum/description/)

## 题解

本题难点主要在于组合不重复性。第一次AC使用了非常tricky的做法，使用Python，先用`set`存储`tuple`，在返回时把`tuple`和`set`再转为`list`，不过，运行时间较长。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 376  ms | N/A |

```python3
class Solution:
    def combinationSum(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        res = set()
        for num in candidates:
            if num == target:
                res.add((num,))
            elif num < target:
                for rst in self.combinationSum(candidates, target - num):
                    res.add(tuple(sorted([num, *rst])))
        return list(map(list, res))
```
