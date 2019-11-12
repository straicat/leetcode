## 179. Largest Number - 最大数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一组非负整数，重新排列它们的顺序使之组成一个最大的整数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <code>[10,2]</code>
<strong>输出:</strong> <code>210</code></pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> <code>[3,30,34,5,9]</code>
<strong>输出:</strong> <code>9534330</code></pre>

<p><strong>说明: </strong>输出结果可能非常大，所以你需要返回一个字符串而不是整数。</p>



-----

题目标签：Sort

题目链接：[LeetCode](https://leetcode.com/problems/largest-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-number/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 876.5 KB |

```cpp
class Solution {
public:
    string largestNumber(vector<int>& nums) {
        vector<string> ns;
        for (int i : nums){
            ns.push_back(to_string(i));
        }
        auto cmp = [](string& s1, string& s2) { return s1+s2 < s2+s1; };
        sort(ns.begin(), ns.end(), cmp);
        string res;
        for (string s : ns) {
            res = s + res;
        }
        // Remove beginning 0
        string nres;
        bool collect = false;
        for (int i=0; i<res.size(); ++i) {
            if (!collect && (i==res.size()-1) || res[i] != '0' ) {
                collect = true;
            }
            if (collect) {
                nres += res[i];
            }
        }
        return nres;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
