## 318. Maximum Product of Word Lengths - 最大单词长度乘积

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串数组&nbsp;<code>words</code>，找到&nbsp;<code>length(word[i]) * length(word[j])</code>&nbsp;的最大值，并且这两个单词不含有公共字母。你可以认为每个单词只包含小写字母。如果不存在这样的两个单词，返回 0。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> <code>[&quot;abcw&quot;,&quot;baz&quot;,&quot;foo&quot;,&quot;bar&quot;,&quot;xtfn&quot;,&quot;abcdef&quot;]</code>
<strong>输出: </strong><code>16 
<strong>解释:</strong> 这两个单词为<strong> </strong></code><code>&quot;abcw&quot;, &quot;xtfn&quot;</code>。</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> <code>[&quot;a&quot;,&quot;ab&quot;,&quot;abc&quot;,&quot;d&quot;,&quot;cd&quot;,&quot;bcd&quot;,&quot;abcd&quot;]</code>
<strong>输出: </strong><code>4 
<strong>解释: </strong></code>这两个单词为 <code>&quot;ab&quot;, &quot;cd&quot;</code>。</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> <code>[&quot;a&quot;,&quot;aa&quot;,&quot;aaa&quot;,&quot;aaaa&quot;]</code>
<strong>输出: </strong><code>0 
<strong>解释: </strong>不存在这样的两个单词。</code></pre>



-----

题目标签：Bit Manipulation

题目链接：[LeetCode](https://leetcode.com/problems/maximum-product-of-word-lengths/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-product-of-word-lengths/description/)

## 题解

如何判断两个单词没有相同的字母呢？

比较快的做法是用位运算，将单词表示为bitmap的形式，然后两个单词做与运算，如果等于0就没有相同的字母。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 24  ms | 1.1 MB |

```cpp
class Solution {
public:
    int maxProduct(vector<string>& words) {
        if (words.size() < 2) {
            return 0;
        }
        vector<int> arr;
        vector<int> lens;
        for (string word : words) {
            int i = 0;
            int l = 0;
            for (char c : word) {
                i |= (1 << (c - 'a'));
                l++;
            }
            arr.push_back(i);
            lens.push_back(l);
        }
        int res = 0;
        for (int i = 0; i < (int)arr.size() - 1; ++i) {
            for (int j = i + 1; j < (int)arr.size(); ++j) {
                // Note: the priority of & is lower than ==
                if ((arr[i] & arr[j]) == 0) {
                    res = max(res, lens[i] * lens[j]);
                }
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
