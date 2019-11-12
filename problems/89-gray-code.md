## 89. Gray Code - 格雷编码

<!--If you want to use the English description, use `question.content` instead-->

<p>格雷编码是一个二进制数字系统，在该系统中，两个连续的数值仅有一个位数的差异。</p>

<p>给定一个代表编码总位数的非负整数<em> n</em>，打印其格雷编码序列。格雷编码序列必须以 0 开头。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong>&nbsp;2
<strong>输出:</strong>&nbsp;<code>[0,1,3,2]</code>
<strong>解释:</strong>
00 - 0
01 - 1
11 - 3
10 - 2

对于给定的&nbsp;<em>n</em>，其格雷编码序列并不唯一。
例如，<code>[0,2,3,1]</code>&nbsp;也是一个有效的格雷编码序列。

00 - 0
10 - 2
11 - 3
01 - 1</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong>&nbsp;0
<strong>输出:</strong>&nbsp;<code>[0]
<strong>解释:</strong> 我们定义</code>格雷编码序列必须以 0 开头。<code>
&nbsp;    给定</code>编码总位数为<code> <em>n</em> 的格雷编码序列，其长度为 2<sup>n</sup></code>。<code>当 <em>n</em> = 0 时，长度为 2<sup>0</sup> = 1。
&nbsp;    因此，当 <em>n</em> = 0 时，其格雷编码序列为 [0]。</code>
</pre>



-----

题目标签：Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/gray-code/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/gray-code/description/)

## 题解

将x的二进制第n位取反：`x^(i<<n)`

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 995.3 KB |

```cpp
class Solution {
public:
    vector<int> res;
    unordered_set<int> vt;
    void dfs(int n, int x) {
        if (res.size() == pow(2, n)) {
            return;
        }
        for (int i=0; i<n; ++i) {
            int nx = x ^ (1 << i);
            if (!vt.count(nx)) {
                res.emplace_back(nx);
                vt.emplace(nx);
                dfs(n, nx);
            }
        }
    }
    
    vector<int> grayCode(int n) {
        int start = 0;
        res.emplace_back(start);
        vt.emplace(start);
        dfs(n , start);
        return res;
    }
};
```
