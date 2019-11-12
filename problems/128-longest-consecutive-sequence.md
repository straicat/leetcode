## 128. Longest Consecutive Sequence - 最长连续序列

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个未排序的整数数组，找出最长连续序列的长度。</p>

<p>要求算法的时间复杂度为&nbsp;<em>O(n)</em>。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong>&nbsp;[100, 4, 200, 1, 3, 2]
<strong>输出:</strong> 4
<strong>解释:</strong> 最长连续序列是 <code>[1, 2, 3, 4]。它的长度为 4。</code></pre>



-----

题目标签：Union Find / Array

题目链接：[LeetCode](https://leetcode.com/problems/longest-consecutive-sequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-consecutive-sequence/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 9.9 MB |

```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_set<int> s;
        s.insert(nums.begin(), nums.end());
        int res = 0;
        for (auto it = s.begin(); it != s.end(); it++) {
            if (s.find(*it - 1) == s.end()) {
                int t = 1;
                for (int i = 1; s.find(*it + i) != s.end(); i++) {
                    t++;
                }
                res = max(res, t);
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
