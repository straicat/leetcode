## 1156. Swap For Longest Repeated Character Substring - 单字符重复子串的最大长度

<!--If you want to use the English description, use `question.content` instead-->

<p>如果字符串中的所有字符都相同，那么这个字符串是单字符重复的字符串。</p>

<p>给你一个字符串&nbsp;<code>text</code>，你只能交换其中两个字符一次或者什么都不做，然后得到一些单字符重复的子串。返回其中最长的子串的长度。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>text = &quot;ababa&quot;
<strong>输出：</strong>3
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>text = &quot;aaabaaa&quot;
<strong>输出：</strong>6
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>text = &quot;aaabbaaa&quot;
<strong>输出：</strong>4
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>text = &quot;aaaaa&quot;
<strong>输出：</strong>5
</pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入：</strong>text = &quot;abcdef&quot;
<strong>输出：</strong>1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= text.length &lt;= 20000</code></li>
	<li><code>text</code> 仅由小写英文字母组成。</li>
</ul>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/swap-for-longest-repeated-character-substring/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/swap-for-longest-repeated-character-substring/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 72  ms | 15.9 MB |

```python3
class Solution:
    def maxRepOpt1(self, text: str) -> int:
        if not text:
            return 0
        rec = collections.defaultdict(list)
        pre = 0
        for i in range(1, len(text)):
            if text[i] != text[pre]:
                rec[text[pre]].append([pre, i])
                pre = i
        rec[text[pre]].append([pre, i + 1])
        # print(rec)
        res = 0
        for rs in rec.values():
            for i in range(len(rs)):
                res = max(res, rs[i][1] - rs[i][0] + (len(rs) > 1))
                if i > 0 and rs[i][0] == rs[i - 1][1] + 1:
                    res = max(res, rs[i][1] - rs[i - 1][0] - (len(rs) < 3))
        return res
```
