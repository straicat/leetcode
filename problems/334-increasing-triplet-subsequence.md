## 334. Increasing Triplet Subsequence - 递增的三元子序列

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个未排序的数组，判断这个数组中是否存在长度为 3 的递增子序列。</p>

<p>数学表达式如下:</p>

<blockquote>如果存在这样的&nbsp;<em>i, j, k,&nbsp;</em>&nbsp;且满足&nbsp;0 &le; <em>i</em> &lt; <em>j</em> &lt; <em>k</em> &le; <em>n</em>-1，<br>
使得&nbsp;<em>arr[i]</em> &lt; <em>arr[j]</em> &lt; <em>arr[k] </em>，返回 true ;&nbsp;否则返回 false 。</blockquote>

<p><strong>说明:</strong> 要求算法的时间复杂度为 O(<em>n</em>)，空间复杂度为 O(<em>1</em>) 。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>[1,2,3,4,5]
<strong>输出: </strong>true
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>[5,4,3,2,1]
<strong>输出: </strong>false</pre>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/increasing-triplet-subsequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/increasing-triplet-subsequence/description/)

## 题解

基于候选的思想。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1.2 MB |

```cpp
class Solution {
public:
    bool increasingTriplet(vector<int>& nums) {
        int c1 = INT_MAX, c2 = INT_MAX;
        for (int n : nums) {
            if (n <= c1) {
                c1 = n;
            } else if (n <= c2) {
                c2 = n;
            } else {
                return true;
            }
        }
        return false;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
