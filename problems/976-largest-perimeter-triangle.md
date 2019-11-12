## 976. Largest Perimeter Triangle - 三角形的最大周长

<!--If you want to use the English description, use `question.content` instead-->

<p>给定由一些正数（代表长度）组成的数组 <code>A</code>，返回由其中三个长度组成的、<strong>面积不为零</strong>的三角形的最大周长。</p>

<p>如果不能形成任何面积不为零的三角形，返回&nbsp;<code>0</code>。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[2,1,2]
<strong>输出：</strong>5
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[1,2,1]
<strong>输出：</strong>0
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>[3,2,3,4]
<strong>输出：</strong>10
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>[3,6,2,3]
<strong>输出：</strong>8
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>3 &lt;= A.length &lt;= 10000</code></li>
	<li><code>1 &lt;= A[i] &lt;= 10^6</code></li>
</ol>



-----

题目标签：Sort / Math

题目链接：[LeetCode](https://leetcode.com/problems/largest-perimeter-triangle/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-perimeter-triangle/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 32  ms | 1.3 MB |

```cpp
class Solution {
public:
    int largestPerimeter(vector<int>& A) {
        if (A.size() < 3) {
            return 0;
        }
        sort(A.begin(), A.end());
        for (int i = A.size() - 3; i >= 0; --i) {
            if (A[i] + A[i+1] > A[i+2]) {
                return A[i] + A[i+1] + A[i+2];
            }
        }
        return 0;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
