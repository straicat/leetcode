## 397. Integer Replacement - 整数替换

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个正整数&nbsp;<em>n</em>，你可以做如下操作：</p>

<p>1. 如果&nbsp;<em>n&nbsp;</em>是偶数，则用&nbsp;<code>n / 2</code>替换&nbsp;<em>n</em>。<br />
2. 如果&nbsp;<em>n&nbsp;</em>是奇数，则可以用&nbsp;<code>n + 1</code>或<code>n - 1</code>替换&nbsp;<em>n</em>。<br />
<em>n&nbsp;</em>变为 1 所需的最小替换次数是多少？</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong>
8

<strong>输出:</strong>
3

<strong>解释:</strong>
8 -&gt; 4 -&gt; 2 -&gt; 1
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong>
7

<strong>输出:</strong>
4

<strong>解释:</strong>
7 -&gt; 8 -&gt; 4 -&gt; 2 -&gt; 1
或
7 -&gt; 6 -&gt; 3 -&gt; 2 -&gt; 1
</pre>



-----

题目标签：Bit Manipulation / Math

题目链接：[LeetCode](https://leetcode.com/problems/integer-replacement/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/integer-replacement/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 774.1 KB |

```cpp
class Solution {
public:
    int integerReplacement(int n) {
        int res = 0;
        long long x = (long long)n;
        for (; x != 1; res++) {
            // Note: the priority of & is lower than ==
            if ((x & 1) == 0) {
                x >>= 1;
            } else if (x == 3 || (x & 3) == 1) {
                x--;
            } else {
                x++;
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
