## 59. Spiral Matrix II - 螺旋矩阵 II

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个正整数&nbsp;<em>n</em>，生成一个包含 1 到&nbsp;<em>n</em><sup>2</sup>&nbsp;所有元素，且元素按顺时针顺序螺旋排列的正方形矩阵。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 3
<strong>输出:</strong>
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]</pre>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/spiral-matrix-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/spiral-matrix-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 925.7 KB |

```cpp
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> res = vector<vector<int>>(n, vector<int>(n, 0));
        if (n < 1) { return res; }
        int x = 0;
        int y = 0;
        int num = 1;
        for (int step=n-1; step>=1; step-=2) {
            for (int i=0; i<step; ++i) {
                res[x][y++] = num++;
            }
            for (int i=0; i<step; ++i) {
                res[x++][y] = num++;
            }
            for (int i=0; i<step; ++i) {
                res[x][y--] = num++;
            }
            for (int i=0; i<step; ++i) {
                res[x--][y] = num++;
            }
            x++;
            y++;
        }
        if (n % 2) {
            res[n/2][n/2] = n * n;
        }
        return res;
    }
};
```
