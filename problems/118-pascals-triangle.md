## 118. Pascal's Triangle - 杨辉三角

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非负整数&nbsp;<em>numRows，</em>生成杨辉三角的前&nbsp;<em>numRows&nbsp;</em>行。</p>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif"></p>

<p><small>在杨辉三角中，每个数是它左上方和右上方的数的和。</small></p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 5
<strong>输出:</strong>
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]</pre>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/pascals-triangle/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/pascals-triangle/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 44  ms | N/A |

```python3
class Solution:
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        res = []
        if numRows == 0:
            return res
        res.append([1])
        if numRows == 1:
            return res
        for l in range(2, numRows+1):
            t = [None] * l
            t[0] = 1
            t[-1] = 1
            for i in range(1, len(t)-1):
                t[i] = res[-1][i] + res[-1][i-1]
            res.append(t)
        return res
```
