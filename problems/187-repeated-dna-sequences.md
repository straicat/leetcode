## 187. Repeated DNA Sequences - 重复的DNA序列

<!--If you want to use the English description, use `question.content` instead-->

<p>所有 DNA 都由一系列缩写为 A，C，G 和 T 的核苷酸组成，例如：&ldquo;ACGAATTCCG&rdquo;。在研究 DNA 时，识别 DNA 中的重复序列有时会对研究非常有帮助。</p>

<p>编写一个函数来查找 DNA 分子中所有出现超过一次的 10 个字母长的序列（子串）。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>s = &quot;AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT&quot;
<strong>输出：</strong>[&quot;AAAAACCCCC&quot;, &quot;CCCCCAAAAA&quot;]</pre>



-----

题目标签：Bit Manipulation / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/repeated-dna-sequences/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/repeated-dna-sequences/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 40  ms | 9.6 MB |

```cpp
class Solution {
public:
    vector<string> findRepeatedDnaSequences(string s) {
        vector<string> res;
        if (s.size() < 10) return res;
        unordered_map<string, int> M;
        for (int i=0; i<=s.size()-10; ++i) {
            M[s.substr(i, 10)]++;
        }
        for (auto m : M) {
            if (m.second > 1) {
                res.push_back(m.first);
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
