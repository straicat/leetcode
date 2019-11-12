## 58. Length of Last Word - 最后一个单词的长度

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个仅包含大小写字母和空格&nbsp;<code>&#39; &#39;</code>&nbsp;的字符串，返回其最后一个单词的长度。</p>

<p>如果不存在最后一个单词，请返回 0&nbsp;。</p>

<p><strong>说明：</strong>一个单词是指由字母组成，但不包含任何空格的字符串。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> &quot;Hello World&quot;
<strong>输出:</strong> 5
</pre>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/length-of-last-word/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/length-of-last-word/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 44  ms | N/A |

```python3
class Solution:
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        a = s.split()
        return len(a[-1]) if a else 0
```
