## 85. Maximal Rectangle - 最大矩形

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个仅包含&nbsp;0 和 1 的二维二进制矩阵，找出只包含 1 的最大矩形，并返回其面积。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>
[
  [&quot;1&quot;,&quot;0&quot;,&quot;1&quot;,&quot;0&quot;,&quot;0&quot;],
  [&quot;1&quot;,&quot;0&quot;,&quot;<strong>1</strong>&quot;,&quot;<strong>1</strong>&quot;,&quot;<strong>1</strong>&quot;],
  [&quot;1&quot;,&quot;1&quot;,&quot;<strong>1</strong>&quot;,&quot;<strong>1</strong>&quot;,&quot;<strong>1</strong>&quot;],
  [&quot;1&quot;,&quot;0&quot;,&quot;0&quot;,&quot;1&quot;,&quot;0&quot;]
]
<strong>输出:</strong> 6</pre>



-----

题目标签：Stack / Array / Hash Table / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/maximal-rectangle/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximal-rectangle/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 52  ms | 11.9 MB |

```cpp
class Solution {
public:
    int maximalRectangle(vector<vector<char>>& matrix) {
        int n = matrix.size();
        if (!n) return 0;
        int m = matrix[0].size();
        if (!m) return 0;
        
        vector<vector<int> > rc(n + 1, vector<int>(m + 1));
        for (int i = 1; i <= n; i++){
            for (int j = 1; j <= m; j++) {
                rc[i][j] = rc[i - 1][j] + rc[i][j - 1] - rc[i - 1][j - 1] + (matrix[i - 1][j - 1] == '1' ? 1 : 0);
            }
        }
        int res = 0;
        vector<vector<int> > dp(n + 1, vector<int>(m + 1));
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= m; j++) {
                dp[i][j] = max(matrix[i - 1][j - 1] == '1' ? 1 : 0, max(dp[i - 1][j], dp[i][j - 1]));
                if (matrix[i - 1][j - 1]) {
                    bool flag = false;
                    for (int x = i - 1; x >= 0; x--) {
                        if (flag) break;
                        for (int y = j - 1; y >= 0; y--) {
                            int t = rc[i][j] - rc[x][j] - rc[i][y] + rc[x][y];
                            if (t == (i - x) * (j - y)) {
                                dp[i][j] = max(dp[i][j], t);
                            } else {
                                if (y == j - 1) {
                                    flag = true;
                                }
                                break;
                            }
                        }
                    }
                }
                res = max(res, dp[i][j]);
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
