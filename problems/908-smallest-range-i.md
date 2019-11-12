## 908. Smallest Range I - 最小差值 I

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组 <code>A</code>，对于每个整数 <code>A[i]</code>，我们可以选择任意&nbsp;<code>x</code> 满足&nbsp;<code>-K &lt;= x &lt;= K</code>，并将&nbsp;<code>x</code>&nbsp;加到&nbsp;<code>A[i]</code>&nbsp;中。</p>

<p>在此过程之后，我们得到一些数组&nbsp;<code>B</code>。</p>

<p>返回 <code>B</code>&nbsp;的最大值和 <code>B</code>&nbsp;的最小值之间可能存在的最小差值。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>A = [1], K = 0
<strong>输出：</strong>0
<strong>解释：</strong>B = [1]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>A = [0,10], K = 2
<strong>输出：</strong>6
<strong>解释：</strong>B = [2,8]
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>A = [1,3,6], K = 3
<strong>输出：</strong>0
<strong>解释：</strong>B = [3,3,3] 或 B = [4,4,4]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 10000</code></li>
	<li><code>0 &lt;= A[i] &lt;= 10000</code></li>
	<li><code>0 &lt;= K &lt;= 10000</code></li>
</ol>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/smallest-range-i/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/smallest-range-i/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 9.8 MB |

```cpp
class Solution {
public:
    int smallestRangeI(vector<int>& A, int K) {
        int low = INT_MAX, high = INT_MIN;
        for (int a : A) {
            low = min(low, a);
            high = max(high, a);
        }
        return max(0, high - K - (low + K));
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 6  ms | 41.2 MB |

```java
class Solution {
    public int smallestRangeI(int[] A, int K) {
        if (A.length < 2) return 0;
        Arrays.sort(A);
        int low = A[0];
        int high = A[A.length - 1];
        return Math.max(0, high - K - (low + K));
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 44  ms | 14.1 MB |

```python3
class Solution:
    def smallestRangeI(self, A: List[int], K: int) -> int:
        return max(0, max(A) - K - (min(A) + K))
```
