## 345. Reverse Vowels of a String - 反转字符串中的元音字母

<!--If you want to use the English description, use `question.content` instead-->

<p>编写一个函数，以字符串作为输入，反转该字符串中的元音字母。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>&quot;hello&quot;
<strong>输出: </strong>&quot;holle&quot;
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>&quot;leetcode&quot;
<strong>输出: </strong>&quot;leotcede&quot;</pre>

<p><strong>说明:</strong><br>
元音字母不包含字母&quot;y&quot;。</p>



-----

题目标签：Two Pointers / String

题目链接：[LeetCode](https://leetcode.com/problems/reverse-vowels-of-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-vowels-of-a-string/description/)

## 题解

将字符串转为字符数组：`list(s)`，不必`[c for c in s]`

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 96  ms | N/A |

```python3
class Solution:
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        ss = [c for c in s]
        tmp = []
        for i, c in enumerate(ss):
            if c.lower() in 'aeiou':
                tmp.append((i, c))
        for ii, (i, c) in enumerate(tmp):
            ss[i] = tmp[-1 * ii -1][1]
        return ''.join(ss)
```
