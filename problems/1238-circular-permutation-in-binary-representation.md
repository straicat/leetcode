## 1238. Circular Permutation in Binary Representation - 循环码排列

<!--If you want to use the English description, use `question.content` instead-->

<p>给你两个整数&nbsp;<code>n</code> 和 <code>start</code>。你的任务是返回任意 <code>(0,1,2,,...,2^n-1)</code> 的排列 <code>p</code>，并且满足：</p>

<ul>
	<li><code>p[0] = start</code></li>
	<li><code>p[i]</code> 和 <code>p[i+1]</code>&nbsp;的二进制表示形式只有一位不同</li>
	<li><code>p[0]</code> 和 <code>p[2^n -1]</code>&nbsp;的二进制表示形式也只有一位不同</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>n = 2, start = 3
<strong>输出：</strong>[3,2,0,1]
<strong>解释：</strong>这个排列的二进制表示是 (11,10,00,01)
     所有的相邻元素都有一位是不同的，另一个有效的排列是 [3,1,0,2]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输出：</strong>n = 3, start = 2
<strong>输出：</strong>[2,6,7,5,4,0,1,3]
<strong>解释：</strong>这个排列的二进制表示是 (010,110,111,101,100,000,001,011)
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 16</code></li>
	<li><code>0 &lt;= start&nbsp;&lt;&nbsp;2^n</code></li>
</ul>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/circular-permutation-in-binary-representation/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/circular-permutation-in-binary-representation/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 412  ms | 119 MB |

```cpp
class Solution {
public:
    void dfs(unordered_set<int>& s, int cur, int n, vector<int>& ret) {
        if (ret.size() == (1 << n)) {
            return;
        }
        for (int i = 0; i < n; i++) {
            if (((cur >> i) & 1) == 0) {
                int r = cur | (1 << i);
                if (s.find(r) == s.end()) {
                    ret.push_back(r);
                    s.insert(r);
                    dfs(s, r, n, ret);
                }
            } else {
                int r = cur & (~(1 << i));
                if (s.find(r) == s.end()) {
                    ret.push_back(r);
                    s.insert(r);
                    dfs(s, r, n, ret);
                }
            }
        }
    }

    vector<int> circularPermutation(int n, int start) {
        vector<int> res;
        unordered_set<int> s;
        res.push_back(start);
        s.insert(start);
        dfs(s, start, n, res);
        return res;
    }
};
```
