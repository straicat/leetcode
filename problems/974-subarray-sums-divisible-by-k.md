## 974. Subarray Sums Divisible by K - 和可被 K 整除的子数组

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组 <code>A</code>，返回其中元素之和可被 <code>K</code>&nbsp;整除的（连续、非空）子数组的数目。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>A = [4,5,0,-2,-3,1], K = 5
<strong>输出：</strong>7
<strong>解释：
</strong>有 7 个子数组满足其元素之和可被 K = 5 整除：
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 30000</code></li>
	<li><code>-10000 &lt;= A[i] &lt;= 10000</code></li>
	<li><code>2 &lt;= K &lt;= 10000</code></li>
</ol>



-----

题目标签：Array / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/subarray-sums-divisible-by-k/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/subarray-sums-divisible-by-k/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 56  ms | 3.9 MB |

```cpp
class Solution {
public:
    int subarraysDivByK(vector<int>& A, int K) {
        if (K == 0) {
            return 0;
        }
        if (A.size() == 0) {
            return 0;
        }
        vector<int> acc;
        acc.push_back(0);
        for (int a : A) {
            acc.push_back(acc.back() + a);
        }
        int res = 0;
        map<int, int> M;
        for (int a : acc) {
            M[a % K]++;
        }
        for (auto m : M) {
            res += m.second * (m.second - 1) / 2;
            if (m.first < 0) {
                int n = M[K + m.first];
                res += m.second * n;
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
