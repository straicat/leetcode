## 1004. Max Consecutive Ones III - 最大连续1的个数 III

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个由若干 <code>0</code> 和 <code>1</code> 组成的数组&nbsp;<code>A</code>，我们最多可以将&nbsp;<code>K</code>&nbsp;个值从 0 变成 1 。</p>

<p>返回仅包含 1 的最长（连续）子数组的长度。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>A = [1,1,1,0,0,0,1,1,1,1,0], K = 2
<strong>输出：</strong>6
<strong>解释： </strong>
[1,1,1,0,0,<strong>1</strong>,1,1,1,1,<strong>1</strong>]
粗体数字从 0 翻转到 1，最长的子数组长度为 6。</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>A = [0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1], K = 3
<strong>输出：</strong>10
<strong>解释：</strong>
[0,0,1,1,<strong>1</strong>,<strong>1</strong>,1,1,1,<strong>1</strong>,1,1,0,0,0,1,1,1,1]
粗体数字从 0 翻转到 1，最长的子数组长度为 10。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 20000</code></li>
	<li><code>0 &lt;= K &lt;= A.length</code></li>
	<li><code>A[i]</code> 为&nbsp;<code>0</code>&nbsp;或&nbsp;<code>1</code>&nbsp;</li>
</ol>



-----

题目标签：Two Pointers / Sliding Window

题目链接：[LeetCode](https://leetcode.com/problems/max-consecutive-ones-iii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/max-consecutive-ones-iii/description/)

## 题解

双指针，滑动窗口的思想

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 44  ms | 13.7 MB |

```cpp
class Solution {
public:
    int longestOnes(vector<int>& A, int K) {
        int p = 0;
        int q = 0;
        int k = K;
        int n = A.size();
        int res = 0;
        while (p >= 0 && p < n && q >= 0 && q < n) {
            if (A[q] == 0) {
                if (k > 0) {
                    k--;
                    res = max(res, q - p + 1);
                    q++;
                } else {
                    if (A[p] == 0) {
                        k++;
                    }
                    p++;
                }
            } else {
                res = max(res, q - p + 1);
                q++;
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
