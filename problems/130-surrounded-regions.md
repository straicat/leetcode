## 130. Surrounded Regions - 被围绕的区域

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二维的矩阵，包含&nbsp;<code>&#39;X&#39;</code>&nbsp;和&nbsp;<code>&#39;O&#39;</code>（<strong>字母 O</strong>）。</p>

<p>找到所有被 <code>&#39;X&#39;</code> 围绕的区域，并将这些区域里所有的&nbsp;<code>&#39;O&#39;</code> 用 <code>&#39;X&#39;</code> 填充。</p>

<p><strong>示例:</strong></p>

<pre>X X X X
X O O X
X X O X
X O X X
</pre>

<p>运行你的函数后，矩阵变为：</p>

<pre>X X X X
X X X X
X X X X
X O X X
</pre>

<p><strong>解释:</strong></p>

<p>被围绕的区间不会存在于边界上，换句话说，任何边界上的&nbsp;<code>&#39;O&#39;</code>&nbsp;都不会被填充为&nbsp;<code>&#39;X&#39;</code>。 任何不在边界上，或不与边界上的&nbsp;<code>&#39;O&#39;</code>&nbsp;相连的&nbsp;<code>&#39;O&#39;</code>&nbsp;最终都会被填充为&nbsp;<code>&#39;X&#39;</code>。如果两个元素在水平或垂直方向相邻，则称它们是&ldquo;相连&rdquo;的。</p>



-----

题目标签：Depth-first Search / Breadth-first Search / Union Find

题目链接：[LeetCode](https://leetcode.com/problems/surrounded-regions/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/surrounded-regions/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 160  ms | 14.4 MB |

```python3
class Solution:
    def solve(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        if not len(board) or not len(board[0]):
            return

        n = len(board)
        m = len(board[0])
        dx = (-1, 1, 0, 0)
        dy = (0, 0, 1, -1)
        
        Q = []
        V = [[0] * m for _ in range(n)]
        for i in range(m):
            if board[0][i] == 'O':
                Q.append((0, i))
                V[0][i] = 1
            if board[n - 1][i] == 'O':
                Q.append((n - 1, i))
                V[n - 1][i] = 1
        for i in range(n):
            if board[i][0] == 'O':
                Q.append((i, 0))
                V[i][0] = 1
            if board[i][m - 1] == 'O':
                Q.append((i, m - 1))
                V[i][m - 1] = 1

        while len(Q):
            p = Q.pop()
            for k in range(4):
                x = p[0] + dx[k]
                y = p[1] + dy[k]
                if 0 <= x < n and 0 <= y < m and board[x][y] == 'O' and not V[x][y]:
                    Q.append((x, y))
                    V[x][y] = 1
        
        for i in range(n):
            for j in range(m):
                if not V[i][j]:
                    board[i][j] = 'X'
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 24  ms | 2.5 MB |

```cpp
class Solution {
public:
    void solve(vector<vector<char>>& board) {
        if (!board.size() || !board[0].size()) return;
        int n = board.size();
        int m = board[0].size();
        vector<vector<int> > A = vector<vector<int> >(n, vector<int>(m, 0));
        set<pair<int, int> > P;
        for (int i=0; i<m; ++i) {
            if (board[0][i] == 'O') {
                A[0][i] = 1;
                P.insert(make_pair(0, i));
            }
        } 
        for (int i=0; i<n; ++i) {
            if (board[i][m-1] == 'O') {
                A[i][m-1] = 1;
                P.insert(make_pair(i, m-1));
            }
        }
        for (int i=0; i<m; ++i) {
            if (board[n-1][i] == 'O') {
                A[n-1][i] = 1;
                P.insert(make_pair(n-1, i));
            }
        }
        for (int i=0; i<n; ++i) {
            if (board[i][0] == 'O') {
                A[i][0] = 1;
                P.insert(make_pair(i, 0));
            }
        }

        queue<pair<int, int> > Q;
        for (auto p : P) {
            // cout << "(" << p.first << ", " << p.second << ")" << endl;
            Q.push(p);
        }
        int dx[] = {0, 1, 0, -1};
        int dy[] = {1, 0, -1, 0};
        while (!Q.empty()) {
            auto p = Q.front();
            Q.pop();
            for (int i=0; i<4; ++i) {
                int nx = p.first + dx[i];
                int ny = p.second + dy[i];
                if (nx >= 0 && nx < n && ny >= 0 && ny < m && board[nx][ny] == 'O' && A[nx][ny] == 0) {
                    Q.push(make_pair(nx, ny));
                    A[nx][ny] = 1;
                }
            }
        }

        for (int i=0; i<n; ++i) 
            for (int j=0; j<m; ++j) 
                if (A[i][j] == 0) 
                    board[i][j] = 'X';
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
