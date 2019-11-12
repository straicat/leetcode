## 812. Largest Triangle Area - 最大三角形面积

<!--If you want to use the English description, use `question.content` instead-->

<p>给定包含多个点的集合，从其中取三个点组成三角形，返回能组成的最大三角形的面积。</p>

<pre>
<strong>示例:</strong>
<strong>输入:</strong> points = [[0,0],[0,1],[1,0],[0,2],[2,0]]
<strong>输出:</strong> 2
<strong>解释:</strong> 
这五个点如下图所示。组成的橙色三角形是最大的，面积为2。
</pre>

<p><img alt="" src="https://s3-lc-upload.s3.amazonaws.com/uploads/2018/04/04/1027.png" style="height:328px; width:400px" /></p>

<p><strong>注意: </strong></p>

<ul>
	<li><code>3 &lt;= points.length &lt;= 50</code>.</li>
	<li>不存在重复的点。</li>
	<li>&nbsp;<code>-50 &lt;= points[i][j] &lt;= 50</code>.</li>
	<li>结果误差值在&nbsp;<code>10^-6</code>&nbsp;以内都认为是正确答案。</li>
</ul>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/largest-triangle-area/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-triangle-area/description/)

## 题解

已知平面三个点的坐标：(x1, y1), (x2, y2), (x3, y3)，围成的三角形面积S=1/2\*（下面这个行列式）

|x1 y1 1|

|x2 y2 1|

|x3 y3 1|

的绝对值。



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 300  ms | N/A |

```python3
class Solution:
    def largestTriangleArea(self, points):
        """
        :type points: List[List[int]]
        :rtype: float
        """
        if len(points) < 3:
            return 0
        res = 0
        for i in range(len(points)-2):
            for j in range(i, len(points)-1):
                for k in range(j, len(points)):
                    res = max(res, self.area(points[i], points[j], points[k]))
        return res
    
    def area(self, p, q, r):
        return 0.5 * abs(p[0]*q[1]+q[0]*r[1]+r[0]*p[1]-p[1]*q[0]-q[1]*r[0]-r[1]*p[0])
```
