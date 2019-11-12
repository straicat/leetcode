## 96. Unique Binary Search Trees - 不同的二叉搜索树

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数 <em>n</em>，求以&nbsp;1 ...&nbsp;<em>n</em>&nbsp;为节点组成的二叉搜索树有多少种？</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 3
<strong>输出:</strong> 5
<strong>解释:
</strong>给定 <em>n</em> = 3, 一共有 5 种不同结构的二叉搜索树:

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3</pre>



-----

题目标签：Tree / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/unique-binary-search-trees/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/unique-binary-search-trees/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 831.5 KB |

```cpp
class Solution {
public:
    int numTrees(int n) {
        /*
          x    0  1  2  3  4
        F(x)   1  1  2  5  14
        3 : 0,2  1,1  2,0
        5 = 1*2 + 1*1 + 2*1
        */
        int dp[n+1] {1};
        for (int x=1; x<=n; ++x) {
            for (int i=0; i<x; ++i) {
                dp[x] += dp[i] * dp[x - 1 - i];
            }
        }
        return dp[n];
    }
};
```
