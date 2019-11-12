## 264. Ugly Number II - 丑数 II

<!--If you want to use the English description, use `question.content` instead-->

<p>编写一个程序，找出第 <code>n</code> 个丑数。</p>

<p>丑数就是只包含质因数&nbsp;<code>2, 3, 5</code> 的<strong>正整数</strong>。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> n = 10
<strong>输出:</strong> 12
<strong>解释: </strong><code>1, 2, 3, 4, 5, 6, 8, 9, 10, 12</code> 是前 10 个丑数。</pre>

<p><strong>说明:&nbsp;</strong>&nbsp;</p>

<ol>
	<li><code>1</code>&nbsp;是丑数。</li>
	<li><code>n</code>&nbsp;<strong>不超过</strong>1690。</li>
</ol>



-----

题目标签：Heap / Math / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/ugly-number-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ugly-number-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 112  ms | 22 MB |

```cpp
class Solution {
public:
    // 缓存所有丑数
    vector<int> nums;

    int nthUglyNumber(int n) {
        if (nums.empty()) {
            for (long a = 1; a <= INT_MAX; a *= 2) {
                for (long b = a; b <= INT_MAX; b *= 3) {
                    for (long c = b; c <= INT_MAX; c *= 5) {
                        nums.push_back(c);
                    }
                }
            }
            sort(nums.begin(), nums.end());
        }
        return nums[n - 1];
    }
};
```
