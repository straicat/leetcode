## 849. Maximize Distance to Closest Person - 到最近的人的最大距离

<!--If you want to use the English description, use `question.content` instead-->

<p>在一排座位（&nbsp;<code>seats</code>）中，<code>1</code>&nbsp;代表有人坐在座位上，<code>0</code>&nbsp;代表座位上是空的。</p>

<p>至少有一个空座位，且至少有一人坐在座位上。</p>

<p>亚历克斯希望坐在一个能够使他与离他最近的人之间的距离达到最大化的座位上。</p>

<p>返回他到离他最近的人的最大距离。</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[1,0,0,0,1,0,1]
<strong>输出：</strong>2
<strong>解释：
</strong>如果亚历克斯坐在第二个空位（seats[2]）上，他到离他最近的人的距离为 2 。
如果亚历克斯坐在其它任何一个空位上，他到离他最近的人的距离为 1 。
因此，他到离他最近的人的最大距离是 2 。 
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[1,0,0,0]
<strong>输出：</strong>3
<strong>解释： </strong>
如果亚历克斯坐在最后一个座位上，他离最近的人有 3 个座位远。
这是可能的最大距离，所以答案是 <span style="">3 </span>。
</pre>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= seats.length &lt;= 20000</code></li>
	<li><code>seats</code>&nbsp;中只含有 0 和 1，至少有一个 <code>0</code>，且至少有一个 <code>1</code>。</li>
</ol>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/maximize-distance-to-closest-person/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximize-distance-to-closest-person/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 84  ms | N/A |

```python3
class Solution:
    def maxDistToClosest(self, seats):
        """
        :type seats: List[int]
        :rtype: int
        """
        tmp = []
        l, r = None, None
        pre = None
        for i, n in enumerate(seats):
            if n == 0:
                if pre != 0:
                    l = i
                    pre = 0
            else:
                if pre == 0:
                    r = i - 1
                    tmp.append((l, r))
                    pre = n
        if n == 0:
            tmp.append((l, i))
        sp = []
        for l, r in tmp:
            if l == 0 or r == len(seats) - 1:
                sp.append(r - l + 1)
            else:
                sp.append((r - l + 2) // 2)
        return max(sp)
```
