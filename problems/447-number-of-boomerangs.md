## 447. Number of Boomerangs - 回旋镖的数量

<!--If you want to use the English description, use `question.content` instead-->

<p>给定平面上<em>&nbsp;n </em>对不同的点，&ldquo;回旋镖&rdquo; 是由点表示的元组&nbsp;<code>(i, j, k)</code>&nbsp;，其中&nbsp;<code>i</code>&nbsp;和&nbsp;<code>j</code>&nbsp;之间的距离和&nbsp;<code>i</code>&nbsp;和&nbsp;<code>k</code>&nbsp;之间的距离相等（<strong>需要考虑元组的顺序</strong>）。</p>

<p>找到所有回旋镖的数量。你可以假设<em>&nbsp;n </em>最大为 <strong>500</strong>，所有点的坐标在闭区间<strong> [-10000, 10000] </strong>中。</p>

<p><strong>示例:</strong></p>

<pre>
<strong>输入:</strong>
[[0,0],[1,0],[2,0]]

<strong>输出:</strong>
2

<strong>解释:</strong>
两个回旋镖为 <strong>[[1,0],[0,0],[2,0]]</strong> 和 <strong>[[1,0],[2,0],[0,0]]</strong>
</pre>



-----

题目标签：Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/number-of-boomerangs/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-boomerangs/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 1720  ms | N/A |

```python3
class Solution:
    def numberOfBoomerangs(self, points):
        """
        :type points: List[List[int]]
        :rtype: int
        """
        if len(points) < 3:
            return 0
        ds = {k: collections.defaultdict(int) for k in range(len(points))}
        for i in range(len(points)-1):
            for j in range(i+1, len(points)):
                d = (points[i][0] - points[j][0]) ** 2 + (points[i][1] - points[j][1]) ** 2
                ds[i][d] += 1
                ds[j][d] += 1
        res = 0
        for point in ds.values():
            for c in point.values():
                if c > 1:
                    res += c * (c - 1)
        return res
```
