## 14. Longest Common Prefix - 最长公共前缀

<!--If you want to use the English description, use `question.content` instead-->

<p>编写一个函数来查找字符串数组中的最长公共前缀。</p>

<p>如果不存在公共前缀，返回空字符串&nbsp;<code>&quot;&quot;</code>。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入: </strong>[&quot;flower&quot;,&quot;flow&quot;,&quot;flight&quot;]
<strong>输出:</strong> &quot;fl&quot;
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入: </strong>[&quot;dog&quot;,&quot;racecar&quot;,&quot;car&quot;]
<strong>输出:</strong> &quot;&quot;
<strong>解释:</strong> 输入不存在公共前缀。
</pre>

<p><strong>说明:</strong></p>

<p>所有输入只包含小写字母&nbsp;<code>a-z</code>&nbsp;。</p>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/longest-common-prefix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-common-prefix/description/)

## 题解

这题很简单，但是容易考虑不周全字符串索引存在性问题。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 52  ms | N/A |

```python3
class Solution:
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        rst = ''
        i = 0
        while True:
            c = []
            for s in strs:
                if len(s) > i:
                    c.append(s[i])
                else:
                    return rst
            c = set(c)
            if len(c) == 1:
                rst += list(c)[0]
                i += 1
            else:
                break
        return rst
```
