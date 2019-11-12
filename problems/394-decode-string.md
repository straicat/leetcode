## 394. Decode String - 字符串解码

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个经过编码的字符串，返回它解码后的字符串。</p>

<p>编码规则为: <code>k[encoded_string]</code>，表示其中方括号内部的 <em>encoded_string</em> 正好重复 <em>k</em> 次。注意 <em>k</em> 保证为正整数。</p>

<p>你可以认为输入字符串总是有效的；输入字符串中没有额外的空格，且输入的方括号总是符合格式要求的。</p>

<p>此外，你可以认为原始数据不包含数字，所有的数字只表示重复的次数 <em>k</em> ，例如不会出现像&nbsp;<code>3a</code>&nbsp;或&nbsp;<code>2[4]</code>&nbsp;的输入。</p>

<p><strong>示例:</strong></p>

<pre>
s = &quot;3[a]2[bc]&quot;, 返回 &quot;aaabcbc&quot;.
s = &quot;3[a2[c]]&quot;, 返回 &quot;accaccacc&quot;.
s = &quot;2[abc]3[cd]ef&quot;, 返回 &quot;abcabccdcdcdef&quot;.
</pre>



-----

题目标签：Stack / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/decode-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/decode-string/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 958.5 KB |

```cpp
class Solution {
public:
    string dfs(string s, int& i) {
        string res = "";
        while (i < s.size() && s[i] != ']') {
            if (s[i] >= 'A') {
                res += s[i++];
            } else {
                int k = 0;
                while (s[i] >= '0' && s[i] <= '9') {
                    k = 10 * k + s[i++] - '0';
                }
                string p = dfs(s, ++i);
                i++;
                for (; k>0; --k) {
                    res += p;
                }
            }
        }
        return res;
    }
    
    string decodeString(string s) {
        int i = 0;
        return dfs(s, i);
    }
};
```
