## 77. Combinations - 组合

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个整数 <em>n</em> 和 <em>k</em>，返回 1 ... <em>n </em>中所有可能的 <em>k</em> 个数的组合。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>&nbsp;n = 4, k = 2
<strong>输出:</strong>
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]</pre>



-----

题目标签：Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/combinations/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combinations/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 196  ms | N/A |

```python3
class Solution:
    def combine(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: List[List[int]]
        """
        return list(itertools.combinations(range(1, n+1), k))
```
