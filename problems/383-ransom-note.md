## 383. Ransom Note - 赎金信

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个赎金信 (ransom) 字符串和一个杂志(magazine)字符串，判断第一个字符串ransom能不能由第二个字符串magazines里面的字符构成。如果可以构成，返回 true ；否则返回 false。</p>

<p>(题目说明：为了不暴露赎金信字迹，要从杂志上搜索各个需要的字母，组成单词来表达意思。)</p>

<p><strong>注意：</strong></p>

<p>你可以假设两个字符串均只含有小写字母。</p>

<pre>
canConstruct(&quot;a&quot;, &quot;b&quot;) -&gt; false
canConstruct(&quot;aa&quot;, &quot;ab&quot;) -&gt; false
canConstruct(&quot;aa&quot;, &quot;aab&quot;) -&gt; true
</pre>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/ransom-note/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ransom-note/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 68  ms | N/A |

```python3
from collections import Counter

class Solution:
    def canConstruct(self, ransomNote, magazine):
        """
        :type ransomNote: str
        :type magazine: str
        :rtype: bool
        """
        c1 = Counter(ransomNote)
        c2 = Counter(magazine)
        for k, v in c1.items():
            if k not in c2 or  v > c2[k]:
                return False
        return True
```
