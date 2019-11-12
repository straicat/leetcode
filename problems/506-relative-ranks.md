## 506. Relative Ranks - 相对名次

<!--If you want to use the English description, use `question.content` instead-->

<p>给出&nbsp;<strong>N</strong> 名运动员的成绩，找出他们的相对名次并授予前三名对应的奖牌。前三名运动员将会被分别授予 &ldquo;金牌&rdquo;，&ldquo;银牌&rdquo; 和&ldquo; 铜牌&rdquo;（&quot;Gold Medal&quot;, &quot;Silver Medal&quot;, &quot;Bronze Medal&quot;）。</p>

<p>(注：分数越高的选手，排名越靠前。)</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [5, 4, 3, 2, 1]
<strong>输出:</strong> [&quot;Gold Medal&quot;, &quot;Silver Medal&quot;, &quot;Bronze Medal&quot;, &quot;4&quot;, &quot;5&quot;]
<strong>解释:</strong> 前三名运动员的成绩为前三高的，因此将会分别被授予 &ldquo;金牌&rdquo;，&ldquo;银牌&rdquo;和&ldquo;铜牌&rdquo; (&quot;Gold Medal&quot;, &quot;Silver Medal&quot; and &quot;Bronze Medal&quot;).
余下的两名运动员，我们只需要通过他们的成绩计算将其相对名次即可。</pre>

<p><strong>提示:</strong></p>

<ol>
	<li>N 是一个正整数并且不会超过&nbsp;10000。</li>
	<li>所有运动员的成绩都不相同。</li>
</ol>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/relative-ranks/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/relative-ranks/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 72  ms | 15 MB |

```python3
class Solution:
    def findRelativeRanks(self, nums: List[int]) -> List[str]:
        score = {s: i + 1 for i, s in enumerate(sorted(nums, reverse=True))}
        return [("Gold Medal", "Silver Medal", "Bronze Medal")[score[s] - 1] if score[s] <= 3 else str(score[s]) for s in nums]
```
