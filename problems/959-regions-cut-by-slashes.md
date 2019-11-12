## 959. Regions Cut By Slashes - 由斜杠划分区域

<!--If you want to use the English description, use `question.content` instead-->

<p>在由 1 x 1 方格组成的 N x N 网格&nbsp;<code>grid</code> 中，每个 1 x 1&nbsp;方块由 <code>/</code>、<code>\</code> 或空格构成。这些字符会将方块划分为一些共边的区域。</p>

<p>（请注意，反斜杠字符是转义的，因此 <code>\</code> 用 <code>&quot;\\&quot;</code>&nbsp;表示。）。</p>

<p>返回区域的数目。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：
</strong>[
&nbsp; &quot; /&quot;,
&nbsp; &quot;/ &quot;
]
<strong>输出：</strong>2
<strong>解释：</strong>2x2 网格如下：
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/15/1.png"></pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：
</strong>[
&nbsp; &quot; /&quot;,
&nbsp; &quot;  &quot;
]
<strong>输出：</strong>1
<strong>解释：</strong>2x2 网格如下：
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/15/2.png"></pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：
</strong>[
&nbsp; &quot;\\/&quot;,
&nbsp; &quot;/\\&quot;
]
<strong>输出：</strong>4
<strong>解释：</strong>（回想一下，因为 \ 字符是转义的，所以 &quot;\\/&quot; 表示 \/，而 &quot;/\\&quot; 表示 /\。）
2x2 网格如下：
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/15/3.png"></pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：
</strong>[
&nbsp; &quot;/\\&quot;,
&nbsp; &quot;\\/&quot;
]
<strong>输出：</strong>5
<strong>解释：</strong>（回想一下，因为 \ 字符是转义的，所以 &quot;/\\&quot; 表示 /\，而 &quot;\\/&quot; 表示 \/。）
2x2 网格如下：
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/15/4.png"></pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入：
</strong>[
&nbsp; &quot;//&quot;,
&nbsp; &quot;/ &quot;
]
<strong>输出：</strong>3
<strong>解释：</strong>2x2 网格如下：
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/15/5.png">
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= grid.length == grid[0].length &lt;= 30</code></li>
	<li><code>grid[i][j]</code> 是&nbsp;<code>&#39;/&#39;</code>、<code>&#39;\&#39;</code>、或&nbsp;<code>&#39; &#39;</code>。</li>
</ol>



-----

题目标签：Depth-first Search / Union Find / Graph

题目链接：[LeetCode](https://leetcode.com/problems/regions-cut-by-slashes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/regions-cut-by-slashes/description/)

## 题解

![image](https://user-images.githubusercontent.com/9983385/54684016-18f8c680-4b4e-11e9-8847-03b6e4dfbe87.png)



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 12  ms | 10.7 MB |

```cpp
class UF {
private:
    vector<int> pre;
public:
    UF(int n) {
        for (int i = 0; i < n; i++)
            pre.push_back(i);
    }
    
    int find(int x) {
        return pre[x] == x ? x : pre[x] = find(pre[x]);
    }
    
    void join(int x, int y) {
        int xr = find(x);
        int yr = find(y);
        if (xr != yr) {
            pre[xr] = yr;
        }
    }
    
    bool connected(int x, int y) {
        return find(x) == find(y);
    }
};


class Solution {
public:
    int regionsBySlashes(vector<string>& grid) {
        int n = grid.size();
        UF uf(n * n * 4);
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                int idx = 4 * n * i + 4 * j;
                if (i > 0)
                    uf.join(idx, idx - 4 * n + 2);
                if (j > 0)
                    uf.join(idx + 3, idx - 3);
                switch (grid[i][j]) {
                    case ' ':
                        uf.join(idx, idx + 1);
                        uf.join(idx + 1, idx + 2);
                        uf.join(idx + 2, idx + 3);
                        break;
                    case '/':
                        uf.join(idx, idx + 3);
                        uf.join(idx + 1, idx + 2);
                        break;
                    default:
                        uf.join(idx, idx + 1);
                        uf.join(idx + 2, idx + 3);
                }
            }
        }
        int res = 0;
        for (int i = 0; i < n * n * 4; i++) {
            res += uf.find(i) == i;
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
