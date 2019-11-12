## 451. Sort Characters By Frequency - 根据字符出现频率排序

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串，请将字符串里的字符按照出现的频率降序排列。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong>
&quot;tree&quot;

<strong>输出:</strong>
&quot;eert&quot;

<strong>解释:
</strong>&#39;e&#39;出现两次，&#39;r&#39;和&#39;t&#39;都只出现一次。
因此&#39;e&#39;必须出现在&#39;r&#39;和&#39;t&#39;之前。此外，&quot;eetr&quot;也是一个有效的答案。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong>
&quot;cccaaa&quot;

<strong>输出:</strong>
&quot;cccaaa&quot;

<strong>解释:
</strong>&#39;c&#39;和&#39;a&#39;都出现三次。此外，&quot;aaaccc&quot;也是有效的答案。
注意&quot;cacaca&quot;是不正确的，因为相同的字母必须放在一起。
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong>
&quot;Aabb&quot;

<strong>输出:</strong>
&quot;bbAa&quot;

<strong>解释:
</strong>此外，&quot;bbaA&quot;也是一个有效的答案，但&quot;Aabb&quot;是不正确的。
注意&#39;A&#39;和&#39;a&#39;被认为是两种不同的字符。
</pre>



-----

题目标签：Heap / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/sort-characters-by-frequency/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sort-characters-by-frequency/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 44  ms | N/A |

```python3
class Solution:
    def frequencySort(self, s):
        """
        :type s: str
        :rtype: str
        """
        res = ''
        for c, n in sorted(list(collections.Counter(s).items()), key=lambda x: -x[1]):
            res += c * n
        return res
```