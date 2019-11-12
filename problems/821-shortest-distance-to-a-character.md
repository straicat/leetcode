## 821. Shortest Distance to a Character - 字符的最短距离

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串&nbsp;<code>S</code>&nbsp;和一个字符&nbsp;<code>C</code>。返回一个代表字符串&nbsp;<code>S</code>&nbsp;中每个字符到字符串&nbsp;<code>S</code>&nbsp;中的字符&nbsp;<code>C</code>&nbsp;的最短距离的数组。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> S = &quot;loveleetcode&quot;, C = &#39;e&#39;
<strong>输出:</strong> [3, 2, 1, 0, 1, 0, 0, 1, 2, 2, 1, 0]
</pre>

<p><strong>说明:</strong></p>

<ol>
	<li>字符串&nbsp;<code>S</code>&nbsp;的长度范围为&nbsp;<code>[1, 10000]</code>。</li>
	<li><code>C</code>&nbsp;是一个单字符，且保证是字符串&nbsp;<code>S</code>&nbsp;里的字符。</li>
	<li><code>S</code>&nbsp;和&nbsp;<code>C</code>&nbsp;中的所有字母均为小写字母。</li>
</ol>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/shortest-distance-to-a-character/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shortest-distance-to-a-character/description/)

## 题解

这题比较简单，先记录C出现的位置，然后再次扫描S，计算与左侧C和右侧C的最小间隔，主要难点在于边界的处理。可以把一个很小和很大的数分别插入到C出现位置数组的两端，这样就可以不额外处理边界了，代码会优雅点。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 48  ms | N/A |

```python3
class Solution:
    def shortestToChar(self, S, C):
        """
        :type S: str
        :type C: str
        :rtype: List[int]
        """
        cps = [-1 * len(S)]
        cps.extend([i for i, s in enumerate(S) if s == C])
        cps.append(2 * len(S))
        p = 1
        res = []
        for i, s in enumerate(S):
            if i < cps[p]:
                res.append(min( i - cps[p-1] , cps[p] - i ))
            else:
                p += 1
                res.append(0)
        return res
```
