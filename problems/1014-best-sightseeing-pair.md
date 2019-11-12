## 1014. Best Sightseeing Pair - 最佳观光组合

<!--If you want to use the English description, use `question.content` instead-->

<p>给定正整数数组&nbsp;<code>A</code>，<code>A[i]</code>&nbsp;表示第 <code>i</code> 个观光景点的评分，并且两个景点&nbsp;<code>i</code> 和&nbsp;<code>j</code>&nbsp;之间的距离为&nbsp;<code>j - i</code>。</p>

<p>一对景点（<code>i &lt; j</code>）组成的观光组合的得分为（<code>A[i] + A[j] + i&nbsp;- j</code>）：景点的评分之和<strong>减去</strong>它们两者之间的距离。</p>

<p>返回一对观光景点能取得的最高分。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[8,1,5,2,6]
<strong>输出：</strong>11
<strong>解释：</strong>i = 0, j = 2, <code>A[i] + A[j] + i - j = 8 + 5 + 0 - 2 = 11</code>
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>2 &lt;= A.length &lt;= 50000</code></li>
	<li><code>1 &lt;= A[i] &lt;= 1000</code></li>
</ol>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/best-sightseeing-pair/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/best-sightseeing-pair/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 4  ms | 48.1 MB |

```java
class Solution {
    public int maxScoreSightseeingPair(int[] A) {
        if (A.length == 0) return 0;
        int[] B = new int[A.length];
        int[] C = new int[A.length];
        C[A.length - 1] = A[A.length - 1] - (A.length - 1);
        for (int i = A.length - 2; i >= 0; i--) {
            B[i] = A[i] + i;
            C[i] = Math.max(C[i + 1], A[i] - i);
        }
        int res = 0;
        for (int i = 0; i < A.length - 1; i++) {
            res = Math.max(res, B[i] + C[i + 1]);
        }
        return res;
    }
}
```
