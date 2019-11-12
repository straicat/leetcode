## 49. Group Anagrams - 字母异位词分组

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> <code>[&quot;eat&quot;, &quot;tea&quot;, &quot;tan&quot;, &quot;ate&quot;, &quot;nat&quot;, &quot;bat&quot;]</code>,
<strong>输出:</strong>
[
  [&quot;ate&quot;,&quot;eat&quot;,&quot;tea&quot;],
  [&quot;nat&quot;,&quot;tan&quot;],
  [&quot;bat&quot;]
]</pre>

<p><strong>说明：</strong></p>

<ul>
	<li>所有输入均为小写字母。</li>
	<li>不考虑答案输出的顺序。</li>
</ul>



-----

题目标签：Hash Table / String

题目链接：[LeetCode](https://leetcode.com/problems/group-anagrams/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/group-anagrams/description/)

## 题解

字母异位词（字母相同，但排列不同的字符串）判断，一般不是做字符统计然后比对统计结果，而是设计一个类似“特征函数”的东西，字母异位词有相同的输出结果。其实这样的特征函数可以很简单：把字符排序一下就行。字母异位词经过字符排序后得到的结果是一样的。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 128  ms | N/A |

```python3
class Solution:
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        d = collections.defaultdict(list)
        for s in strs:
            d[''.join(sorted(s))].append(s)
        return list(d.values())
```
