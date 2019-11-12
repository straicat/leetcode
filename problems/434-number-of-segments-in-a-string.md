## 434. Number of Segments in a String - 字符串中的单词数

<!--If you want to use the English description, use `question.content` instead-->

<p>统计字符串中的单词个数，这里的单词指的是连续的不是空格的字符。</p>

<p>请注意，你可以假定字符串里不包括任何不可打印的字符。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> &quot;Hello, my name is John&quot;
<strong>输出:</strong> 5
</pre>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/number-of-segments-in-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-segments-in-a-string/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 32  ms | N/A |

```python3
class Solution:
    def countSegments(self, s):
        """
        :type s: str
        :rtype: int
        """
        return len(s.split())
```
