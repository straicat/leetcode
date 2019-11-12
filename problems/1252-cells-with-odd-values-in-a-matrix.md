## 1252. Cells with Odd Values in a Matrix - 奇数值单元格的数目

<!--If you want to use the English description, use `question.content` instead-->

<p>给你一个&nbsp;<code>n</code>&nbsp;行&nbsp;<code>m</code>&nbsp;列的矩阵，最开始的时候，每个单元格中的值都是 <code>0</code>。</p>

<p>另有一个索引数组&nbsp;<code>indices</code>，<code>indices[i] = [ri, ci]</code>&nbsp;中的&nbsp;<code>ri</code> 和 <code>ci</code> 分别表示指定的行和列（从 <code>0</code> 开始编号）。</p>

<p>你需要将每对&nbsp;<code>[ri, ci]</code>&nbsp;指定的行和列上的所有单元格的值加 <code>1</code>。</p>

<p>请你在执行完所有&nbsp;<code>indices</code>&nbsp;指定的增量操作后，返回矩阵中 「奇数值单元格」 的数目。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/11/06/e1.png" style="height: 118px; width: 600px;"></p>

<pre><strong>输入：</strong>n = 2, m = 3, indices = [[0,1],[1,1]]
<strong>输出：</strong>6
<strong>解释：</strong>最开始的矩阵是 [[0,0,0],[0,0,0]]。
第一次增量操作后得到 [[1,2,1],[0,1,0]]。
最后的矩阵是 [[1,3,1],[1,3,1]]，里面有 6 个奇数。
</pre>

<p><strong>示例 2：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/11/06/e2.png" style="height: 150px; width: 600px;"></p>

<pre><strong>输入：</strong>n = 2, m = 2, indices = [[1,1],[0,0]]
<strong>输出：</strong>0
<strong>解释：</strong>最后的矩阵是 [[2,2],[2,2]]，里面没有奇数。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 50</code></li>
	<li><code>1 &lt;= m &lt;= 50</code></li>
	<li><code>1 &lt;= indices.length &lt;= 100</code></li>
	<li><code>0 &lt;= indices[i][0] &lt;&nbsp;n</code></li>
	<li><code>0 &lt;= indices[i][1] &lt;&nbsp;m</code></li>
</ul>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/cells-with-odd-values-in-a-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/cells-with-odd-values-in-a-matrix/description/)

## 题解

直接模拟即可

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 9.4 MB |

```cpp
class Solution {
public:
    void addCells(vector<vector<int>>& arr, int n, int m, vector<int>& indice) {
        for (int i = 0; i < m; i++) {
            arr[indice[0]][i]++;
        }
        for (int i = 0; i < n; i++) {
            arr[i][indice[1]]++;
        }
    }

    int oddCells(int n, int m, vector<vector<int>>& indices) {
        vector<vector<int>> arr(n, vector<int>(m));
        for (vector<int>& indice : indices) {
            addCells(arr, n, m, indice);
        }
        int res = 0;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (arr[i][j] & 1) {
                    res++;
                }
            }
        }
        return res;
    }
};
```
