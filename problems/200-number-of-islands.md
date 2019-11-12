## 200. Number of Islands - 岛屿数量

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个由&nbsp;<code>&#39;1&#39;</code>（陆地）和 <code>&#39;0&#39;</code>（水）组成的的二维网格，计算岛屿的数量。一个岛被水包围，并且它是通过水平方向或垂直方向上相邻的陆地连接而成的。你可以假设网格的四个边均被水包围。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong>
11110
11010
11000
00000

<strong>输出:</strong>&nbsp;1
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong>
11000
11000
00100
00011

<strong>输出: </strong>3
</pre>



-----

题目标签：Depth-first Search / Breadth-first Search / Union Find

题目链接：[LeetCode](https://leetcode.com/problems/number-of-islands/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-islands/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 2.6 MB |

```cpp
class Solution {
public:
    void dfs(vector<vector<char>>& grid, int r, int c, int n, int m) {
        if (grid[r][c] != '1') {
            return;
        }
        grid[r][c] = '2';
        int dx[] = {-1, 0, 1, 0};
        int dy[] = {0, 1, 0, -1};
        for (int i=0; i<4; ++i) {
            int nr = r + dx[i];
            int nc = c + dy[i];
            if (nr >= 0 && nr < n && nc >= 0 && nc < m && grid[nr][nc] == '1') {
                dfs(grid, nr, nc, n, m);
            }
        }
    }

    int numIslands(vector<vector<char>>& grid) {
        if (!grid.size() || !grid[0].size()) return 0;
        int res = 0;
        int n = grid.size();
        int m = grid[0].size();
        for (int i=0; i<n; ++i) {
            for (int j=0; j<m; ++j) {
                if (grid[i][j] == '1') {
                    res++;
                    dfs(grid, i, j, n, m);
                }
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
