## 1033. Moving Stones Until Consecutive - 移动石子直到连续

<!--If you want to use the English description, use `question.content` instead-->

<p>三枚石子放置在数轴上，位置分别为 <code>a</code>，<code>b</code>，<code>c</code>。</p>

<p>每一回合，我们假设这三枚石子当前分别位于位置 <code>x, y, z</code> 且 <code>x &lt; y &lt; z</code>。从位置 <code>x</code> 或者是位置 <code>z</code> 拿起一枚石子，并将该石子移动到某一整数位置 <code>k</code> 处，其中 <code>x &lt; k &lt; z</code> 且 <code>k != y</code>。</p>

<p>当你无法进行任何移动时，即，这些石子的位置连续时，游戏结束。</p>

<p>要使游戏结束，你可以执行的最小和最大移动次数分别是多少？ 以长度为 2 的数组形式返回答案：<code>answer = [minimum_moves, maximum_moves]</code></p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>a = 1, b = 2, c = 5
<strong>输出：</strong>[1, 2]
<strong>解释：</strong>将石子从 5 移动到 4 再移动到 3，或者我们可以直接将石子移动到 3。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>a = 4, b = 3, c = 2
<strong>输出：</strong>[0, 0]
<strong>解释：</strong>我们无法进行任何移动。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= a &lt;= 100</code></li>
	<li><code>1 &lt;= b &lt;= 100</code></li>
	<li><code>1 &lt;= c &lt;= 100</code></li>
	<li><code>a != b, b != c, c != a</code></li>
</ol>



-----

题目标签：Brainteaser

题目链接：[LeetCode](https://leetcode.com/problems/moving-stones-until-consecutive/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/moving-stones-until-consecutive/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | 13.1 MB |

```python3
class Solution:
    def numMovesStones(self, a: int, b: int, c: int) -> List[int]:
        arr = [a, b, c]
        arr.sort()
        r2 = (arr[1] - arr[0] - 1) + (arr[2] - arr[1] - 1)
        if not r2:
            r1 = 0
        else:
            if arr[1] - arr[0] > 2 and arr[2] - arr[1] > 2:
                r1 = 2
            else:
                r1 = 1
        return [r1, r2]
```
