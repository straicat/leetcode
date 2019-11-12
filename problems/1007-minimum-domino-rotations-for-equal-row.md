## 1007. Minimum Domino Rotations For Equal Row - 行相等的最少多米诺旋转

<!--If you want to use the English description, use `question.content` instead-->

<p>在一排多米诺骨牌中，<code>A[i]</code> 和 <code>B[i]</code>&nbsp;分别代表第 i 个多米诺骨牌的上半部分和下半部分。（一个多米诺是两个从 1 到 6 的数字同列平铺形成的&nbsp;&mdash;&mdash; 该平铺的每一半上都有一个数字。）</p>

<p>我们可以旋转第&nbsp;<code>i</code>&nbsp;张多米诺，使得&nbsp;<code>A[i]</code> 和&nbsp;<code>B[i]</code>&nbsp;的值交换。</p>

<p>返回能使 <code>A</code> 中所有值或者 <code>B</code> 中所有值都相同的最小旋转次数。</p>

<p>如果无法做到，返回&nbsp;<code>-1</code>.</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/03/08/domino.png" style="height: 161px; width: 200px;"></p>

<pre><strong>输入：</strong>A = [2,1,2,4,2,2], B = [5,2,6,2,3,2]
<strong>输出：</strong>2
<strong>解释：</strong>
图一表示：在我们旋转之前， A 和 B 给出的多米诺牌。
如果我们旋转第二个和第四个多米诺骨牌，我们可以使上面一行中的每个值都等于 2，如图二所示。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>A = [3,5,1,2,3], B = [3,6,3,3,4]
<strong>输出：</strong>-1
<strong>解释：</strong>
在这种情况下，不可能旋转多米诺牌使一行的值相等。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A[i], B[i] &lt;= 6</code></li>
	<li><code>2 &lt;= A.length == B.length &lt;= 20000</code></li>
</ol>



-----

题目标签：Greedy / Array

题目链接：[LeetCode](https://leetcode.com/problems/minimum-domino-rotations-for-equal-row/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-domino-rotations-for-equal-row/description/)

## 题解

![image](https://user-images.githubusercontent.com/9983385/54607904-7aeff800-4a8a-11e9-93c8-f28385cec150.png)

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 92  ms | 19.6 MB |

```cpp
class Solution {
public:
    int minDominoRotations(vector<int>& A, vector<int>& B) {
        vector<bool> flag(6, true);
        vector<int> aTimes(6, 0);
        vector<int> bTimes(6, 0);
        int n = max(A.size(), B.size());
        for (int i = 0; i < n; i++) {
            for (int j = 1; j < 7; j++) {
                if ((i >= A.size() || j != A[i]) && (i >= B.size() || j != B[i])) {
                    flag[j-1] = false;
                }
            }
            if (i < A.size())
                aTimes[A[i]-1]++;
            if (i < B.size())
                bTimes[B[i]-1]++;
        }
        bool can = false;
        int res = INT_MAX;
        for (int i = 0; i < 6; i++) {
            if (flag[i]) {
                can = true;
                res = min(res, n - aTimes[i]);
                res = min(res, n - bTimes[i]);
            }
        }
        if (can) {
            return res;
        } else {
            return -1;
        }
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
