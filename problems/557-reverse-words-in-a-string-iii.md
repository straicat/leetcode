## 557. Reverse Words in a String III - 反转字符串中的单词 III

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>
输入: &quot;Let&#39;s take LeetCode contest&quot;
输出: &quot;s&#39;teL ekat edoCteeL tsetnoc&quot;<strong><strong><strong>&nbsp;</strong></strong></strong>
</pre>

<p><strong><strong><strong><strong>注意：</strong></strong></strong></strong>在字符串中，每个单词由单个空格分隔，并且字符串中不会有任何额外的空格。</p>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/reverse-words-in-a-string-iii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-words-in-a-string-iii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 56  ms | N/A |

```python3
class Solution:
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        return ' '.join([w[::-1] for w in s.split()])
```
