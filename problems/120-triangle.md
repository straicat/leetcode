## 120. Triangle - 三角形最小路径和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个三角形，找出自顶向下的最小路径和。每一步只能移动到下一行中相邻的结点上。</p>

<p>例如，给定三角形：</p>

<pre>[
     [<strong>2</strong>],
    [<strong>3</strong>,4],
   [6,<strong>5</strong>,7],
  [4,<strong>1</strong>,8,3]
]
</pre>

<p>自顶向下的最小路径和为&nbsp;<code>11</code>（即，<strong>2&nbsp;</strong>+&nbsp;<strong>3</strong>&nbsp;+&nbsp;<strong>5&nbsp;</strong>+&nbsp;<strong>1</strong>&nbsp;= 11）。</p>

<p><strong>说明：</strong></p>

<p>如果你可以只使用 <em>O</em>(<em>n</em>)&nbsp;的额外空间（<em>n</em> 为三角形的总行数）来解决这个问题，那么你的算法会很加分。</p>



-----

题目标签：Array / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/triangle/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/triangle/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1.5 MB |

```cpp
class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) {
        vector<vector<int> > dp;
        for (int depth=0; depth<triangle.size(); ++depth) {
            dp.push_back(vector<int>());
            for (int i=0; i<triangle[depth].size(); ++i) {
                if (depth==0) {
                    dp[0].push_back(triangle[0][0]);
                    continue;
                }
                int x = triangle[depth][i];
                if (i-1 >= 0 && i<triangle[depth].size()-1) {
                    x += min(dp[depth-1][i-1], dp[depth-1][i]);
                } else {
                    if (i-1 >= 0) x += dp[depth-1][i-1];
                    if (i<triangle[depth].size()-1) x += dp[depth-1][i];
                }
                dp[depth].push_back(x);
            }
        }
        return *min_element(dp.back().begin(), dp.back().end());
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
