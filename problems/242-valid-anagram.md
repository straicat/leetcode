## 242. Valid Anagram - 有效的字母异位词

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个字符串 <em>s</em> 和 <em>t</em> ，编写一个函数来判断 <em>t</em> 是否是 <em>s</em> 的字母异位词。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> <em>s</em> = &quot;anagram&quot;, <em>t</em> = &quot;nagaram&quot;
<strong>输出:</strong> true
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> <em>s</em> = &quot;rat&quot;, <em>t</em> = &quot;car&quot;
<strong>输出: </strong>false</pre>

<p><strong>说明:</strong><br>
你可以假设字符串只包含小写字母。</p>

<p><strong>进阶:</strong><br>
如果输入字符串包含 unicode 字符怎么办？你能否调整你的解法来应对这种情况？</p>



-----

题目标签：Sort / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/valid-anagram/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/valid-anagram/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 72  ms | N/A |

```python3
class Solution:
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        return sorted(list(s)) == sorted(list(t))
```
