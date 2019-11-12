## 983. Minimum Cost For Tickets - 最低票价

<!--If you want to use the English description, use `question.content` instead-->

<p>在一个火车旅行很受欢迎的国度，你提前一年计划了一些火车旅行。在接下来的一年里，你要旅行的日子将以一个名为&nbsp;<code>days</code>&nbsp;的数组给出。每一项是一个从&nbsp;<code>1</code>&nbsp;到&nbsp;<code>365</code>&nbsp;的整数。</p>

<p>火车票有三种不同的销售方式：</p>

<ul>
	<li>一张为期一天的通行证售价为&nbsp;<code>costs[0]</code> 美元；</li>
	<li>一张为期七天的通行证售价为&nbsp;<code>costs[1]</code> 美元；</li>
	<li>一张为期三十天的通行证售价为&nbsp;<code>costs[2]</code> 美元。</li>
</ul>

<p>通行证允许数天无限制的旅行。 例如，如果我们在第 2 天获得一张为期 7 天的通行证，那么我们可以连着旅行 7 天：第 2 天、第 3 天、第 4 天、第 5 天、第 6 天、第 7 天和第 8 天。</p>

<p>返回你想要完成在给定的列表&nbsp;<code>days</code>&nbsp;中列出的每一天的旅行所需要的最低消费。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>days = [1,4,6,7,8,20], costs = [2,7,15]
<strong>输出：</strong>11
<strong>解释： </strong>
例如，这里有一种购买通行证的方法，可以让你完成你的旅行计划：
在第 1 天，你花了 costs[0] = $2 买了一张为期 1 天的通行证，它将在第 1 天生效。
在第 3 天，你花了 costs[1] = $7 买了一张为期 7 天的通行证，它将在第 3, 4, ..., 9 天生效。
在第 20 天，你花了 costs[0] = $2 买了一张为期 1 天的通行证，它将在第 20 天生效。
你总共花了 $11，并完成了你计划的每一天旅行。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>days = [1,2,3,4,5,6,7,8,9,10,30,31], costs = [2,7,15]
<strong>输出：</strong>17
<strong>解释：
</strong>例如，这里有一种购买通行证的方法，可以让你完成你的旅行计划： 
在第 1 天，你花了 costs[2] = $15 买了一张为期 30 天的通行证，它将在第 1, 2, ..., 30 天生效。
在第 31 天，你花了 costs[0] = $2 买了一张为期 1 天的通行证，它将在第 31 天生效。 
你总共花了 $17，并完成了你计划的每一天旅行。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= days.length &lt;= 365</code></li>
	<li><code>1 &lt;= days[i] &lt;= 365</code></li>
	<li><code>days</code>&nbsp;按顺序严格递增</li>
	<li><code>costs.length == 3</code></li>
	<li><code>1 &lt;= costs[i] &lt;= 1000</code></li>
</ol>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/minimum-cost-for-tickets/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-cost-for-tickets/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 2  ms | 36.7 MB |

```java
class Solution {
    
    // 二分搜索上一张有效票
    int search(int[] days, int i, int t) {
        int l = 0, r = i - 1;
        while (l < r) {
            int mid = (l + r) >> 1;
            if (days[i] - days[mid] <= t) r = mid;
            else l = mid + 1;
        }
        return days[i] - days[l] <= t ? l : -1;
    }

    public int mincostTickets(int[] days, int[] costs) {
        int[][] dp = new int[days.length][4];
        int INF = 0x3f3f3f3f;
        
        for (int i = 0; i < days.length; i++) {
            dp[i][3] = INF;
            if (i == 0) {
                for (int j = 0; j < 3; j++)
                    dp[i][j] = costs[j];
            } else {
                // 新买一张票
                int t = INF;
                for (int j = 0; j <= 3; j++)
                    t = Math.min(t, dp[i-1][j]);
                for (int j = 0; j < 3; j++)
                    dp[i][j] = t + costs[j];
                // 使用上一张有效票
                int x = search(days, i, 6);
                if (x != -1)
                    dp[i][3] = Math.min(dp[i][3], dp[x][1]);
                int y = search(days, i, 29);
                if (y != -1)
                    dp[i][3] = Math.min(dp[i][3], dp[y][2]);
            }
        }

        int res = INF;
        for (int j = 0; j <= 3; j++)
            res = Math.min(res, dp[days.length - 1][j]);
        return res;
    }
}
```
