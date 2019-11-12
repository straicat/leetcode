## 539. Minimum Time Difference - 最小时间差

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个 24 小时制（小时:分钟）的时间列表，找出列表中任意两个时间的最小时间差并已分钟数表示。</p>

<p><br />
<strong>示例 1：</strong></p>

<pre>
<strong>输入:</strong> [&quot;23:59&quot;,&quot;00:00&quot;]
<strong>输出:</strong> 1
</pre>

<p><br />
<strong>备注:</strong></p>

<ol>
	<li>列表中时间数在 2~20000 之间。</li>
	<li>每个时间取值在 00:00~23:59 之间。</li>
</ol>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/minimum-time-difference/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-time-difference/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 60  ms | 15.7 MB |

```python3
class Solution:
    def findMinDifference(self, timePoints: List[str]) -> int:
        times = [h * 60 + m for (h, m) in map(lambda tp : tuple(map(int, tp.split(':'))), timePoints)]
        times.sort()
        times.append(1440 + times[0])
        return min([b - a for a, b in zip(times, times[1:])])
```
