## 1185. Day of the Week - 一周中的第几天

<!--If you want to use the English description, use `question.content` instead-->

<p>给你一个日期，请你设计一个算法来判断它是对应一周中的哪一天。</p>

<p>输入为三个整数：<code>day</code>、<code>month</code> 和&nbsp;<code>year</code>，分别表示日、月、年。</p>

<p>您返回的结果必须是这几个值中的一个&nbsp;<code>{&quot;Sunday&quot;, &quot;Monday&quot;, &quot;Tuesday&quot;, &quot;Wednesday&quot;, &quot;Thursday&quot;, &quot;Friday&quot;, &quot;Saturday&quot;}</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>day = 31, month = 8, year = 2019
<strong>输出：</strong>&quot;Saturday&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>day = 18, month = 7, year = 1999
<strong>输出：</strong>&quot;Sunday&quot;
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>day = 15, month = 8, year = 1993
<strong>输出：</strong>&quot;Sunday&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>给出的日期一定是在&nbsp;<code>1971</code> 到&nbsp;<code>2100</code>&nbsp;年之间的有效日期。</li>
</ul>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/day-of-the-week/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/day-of-the-week/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 32  ms | 14 MB |

```python3
from datetime import date

class Solution:
    def dayOfTheWeek(self, day: int, month: int, year: int) -> str:
        rs = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"]
        return rs[date(year, month, day).weekday()]
```
