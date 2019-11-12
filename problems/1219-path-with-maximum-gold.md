## 1219. Path with Maximum Gold - 黄金矿工

<!--If you want to use the English description, use `question.content` instead-->

<p>你要开发一座金矿，地质勘测学家已经探明了这座金矿中的资源分布，并用大小为&nbsp;<code>m * n</code> 的网格 <code>grid</code> 进行了标注。每个单元格中的整数就表示这一单元格中的黄金数量；如果该单元格是空的，那么就是 <code>0</code>。</p>

<p>为了使收益最大化，矿工需要按以下规则来开采黄金：</p>

<ul>
	<li>每当矿工进入一个单元，就会收集该单元格中的所有黄金。</li>
	<li>矿工每次可以从当前位置向上下左右四个方向走。</li>
	<li>每个单元格只能被开采（进入）一次。</li>
	<li><strong>不得开采</strong>（进入）黄金数目为 <code>0</code> 的单元格。</li>
	<li>矿工可以从网格中 <strong>任意一个</strong> 有黄金的单元格出发或者是停止。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>grid = [[0,6,0],[5,8,7],[0,9,0]]
<strong>输出：</strong>24
<strong>解释：</strong>
[[0,6,0],
 [5,8,7],
 [0,9,0]]
一种收集最多黄金的路线是：9 -&gt; 8 -&gt; 7。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>grid = [[1,0,7],[2,0,6],[3,4,5],[0,3,0],[9,0,20]]
<strong>输出：</strong>28
<strong>解释：</strong>
[[1,0,7],
 [2,0,6],
 [3,4,5],
 [0,3,0],
 [9,0,20]]
一种收集最多黄金的路线是：1 -&gt; 2 -&gt; 3 -&gt; 4 -&gt; 5 -&gt; 6 -&gt; 7。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= grid.length,&nbsp;grid[i].length &lt;= 15</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 100</code></li>
	<li>最多 <strong>25 </strong>个单元格中有黄金。</li>
</ul>



-----

题目标签：Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/path-with-maximum-gold/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/path-with-maximum-gold/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 48  ms | 9.5 MB |

```cpp
int dx[] = {-1, 1, 0, 0};
int dy[] = {0, 0, 1, -1};
int n, m;

class Solution {
public:
    int getGold(vector<vector<int>>& grid, int x, int y) {
        int res = grid[x][y];
        grid[x][y] = 0;
        int t = 0;
        for (int k = 0; k < 4; k++) {
            int nx = x + dx[k];
            int ny = y + dy[k];
            if (nx >= 0 && nx < n && ny >= 0 && ny < m && grid[nx][ny]) {
                int tmp = grid[nx][ny];
                t = max(t, getGold(grid, nx, ny));
                grid[nx][ny] = tmp;
            }
        }
        return res + t;
    }

    int getMaximumGold(vector<vector<int>>& grid) {
        if (!(n = grid.size()) || !(m = grid[0].size())) return 0;
        
        int res = 0;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (grid[i][j]) {
                    auto g = grid;
                    int r = getGold(g, i, j);
                    // cout << r << endl;
                    res = max(res, r);
                }
            }
        }
        return res;
    }
};
```
