## 500. Keyboard Row - 键盘行

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个单词列表，只返回可以使用在键盘同一行的字母打印出来的单词。键盘如下图所示。</p>

<p>&nbsp;</p>

<p><img alt="American keyboard" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/keyboard.png" style="width: 100%; max-width: 600px"></p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入:</strong> [&quot;Hello&quot;, &quot;Alaska&quot;, &quot;Dad&quot;, &quot;Peace&quot;]
<strong>输出:</strong> [&quot;Alaska&quot;, &quot;Dad&quot;]
</pre>

<p>&nbsp;</p>

<p><strong>注意：</strong></p>

<ol>
	<li>你可以重复使用键盘上同一字符。</li>
	<li>你可以假设输入的字符串将只包含字母。</li>
</ol>


-----

题目标签：Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/keyboard-row/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/keyboard-row/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 40  ms | N/A |

```python3
class Solution:
    def findWords(self, words):
        """
        :type words: List[str]
        :rtype: List[str]
        """
        d = {}
        for i, s in enumerate('qwertyuiop asdfghjkl zxcvbnm'.split()):
            d.update({k: i for k in s})
        res = []
        for word in words:
            if len(set([d[c.lower()] for c in word])) == 1:
                res.append(word)
        return res
```
