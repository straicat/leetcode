## 1253. Reconstruct a 2-Row Binary Matrix - 重构 2 行二进制矩阵

<!--If you want to use the English description, use `question.content` instead-->

<p>给你一个&nbsp;<code>2</code>&nbsp;行 <code>n</code> 列的二进制数组：</p>

<ul>
	<li>矩阵是一个二进制矩阵，这意味着矩阵中的每个元素不是&nbsp;<code>0</code>&nbsp;就是&nbsp;<code>1</code>。</li>
	<li>第 <code>0</code> 行的元素之和为&nbsp;<code>upper</code>。</li>
	<li>第 <code>1</code> 行的元素之和为 <code>lower</code>。</li>
	<li>第 <code>i</code> 列（从 <code>0</code> 开始编号）的元素之和为&nbsp;<code>colsum[i]</code>，<code>colsum</code>&nbsp;是一个长度为&nbsp;<code>n</code>&nbsp;的整数数组。</li>
</ul>

<p>你需要利用&nbsp;<code>upper</code>，<code>lower</code>&nbsp;和&nbsp;<code>colsum</code>&nbsp;来重构这个矩阵，并以二维整数数组的形式返回它。</p>

<p>如果有多个不同的答案，那么任意一个都可以通过本题。</p>

<p>如果不存在符合要求的答案，就请返回一个空的二维数组。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>upper = 2, lower = 1, colsum = [1,1,1]
<strong>输出：</strong>[[1,1,0],[0,0,1]]
<strong>解释：</strong>[[1,0,1],[0,1,0]] 和 [[0,1,1],[1,0,0]] 也是正确答案。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>upper = 2, lower = 3, colsum = [2,2,1,1]
<strong>输出：</strong>[]
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>upper = 5, lower = 5, colsum = [2,1,2,0,1,0,1,2,0,1]
<strong>输出：</strong>[[1,1,1,0,1,0,0,1,0,0],[1,0,1,0,0,0,1,1,0,1]]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= colsum.length &lt;= 10^5</code></li>
	<li><code>0 &lt;= upper, lower &lt;= colsum.length</code></li>
	<li><code>0 &lt;= colsum[i] &lt;= 2</code></li>
</ul>



-----

题目标签：Greedy / Math

题目链接：[LeetCode](https://leetcode.com/problems/reconstruct-a-2-row-binary-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reconstruct-a-2-row-binary-matrix/description/)

## 题解

由于只需要任一合理解，使用贪心算法即可。

如果colsum的元素为2，说明upper和lower的对应位置都是1

如果colsum的元素为1，优先使upper中的对应位置为1



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 300  ms | 21.8 MB |

```cpp
class Solution {
public:
    vector<vector<int>> reconstructMatrix(int upper, int lower, vector<int>& colsum) {
        int ones = 0;
        int twos = 0;
        for (int col : colsum) {
            if (col == 1) ones++;
            else if (col == 2) twos++;
        }
        int n = colsum.size();
        vector<vector<int>> nil;
        if (ones + 2 * twos != upper + lower || twos > upper || twos > lower) {
            return nil;
        }
        vector<vector<int>> res(2, vector<int>(n));
        int up = 0, low = 0;
        for (int i = 0; i < n; i++) {
            if (colsum[i] == 2) {
                res[0][i] = 1;
                up++;
                res[1][i] = 1;
                low++;
            }
        }
        int j = 0;
        while (up < upper) {
            if (res[0][j] == 0 && colsum[j] == 1) {
                res[0][j] = 1;
                up++;
            }
            j++;
        }
        while (low < lower) {
            if (res[1][j] == 0 && colsum[j] == 1) {
                res[1][j] = 1;
                low++;
            }
            j++;
        }
        return res;
    }
};
```
