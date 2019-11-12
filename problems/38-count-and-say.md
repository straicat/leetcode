## 38. Count and Say - 报数

<!--If you want to use the English description, use `question.content` instead-->

<p>报数序列是一个整数序列，按照其中的整数的顺序进行报数，得到下一个数。其前五项如下：</p>

<pre>1.     1
2.     11
3.     21
4.     1211
5.     111221
</pre>

<p><code>1</code>&nbsp;被读作&nbsp;&nbsp;<code>&quot;one 1&quot;</code>&nbsp;&nbsp;(<code>&quot;一个一&quot;</code>) , 即&nbsp;<code>11</code>。<br>
<code>11</code> 被读作&nbsp;<code>&quot;two 1s&quot;</code>&nbsp;(<code>&quot;两个一&quot;</code>）, 即&nbsp;<code>21</code>。<br>
<code>21</code> 被读作&nbsp;<code>&quot;one 2&quot;</code>, &nbsp;&quot;<code>one 1&quot;</code>&nbsp;（<code>&quot;一个二&quot;</code>&nbsp;,&nbsp;&nbsp;<code>&quot;一个一&quot;</code>)&nbsp;, 即&nbsp;<code>1211</code>。</p>

<p>给定一个正整数 <em>n</em>（1 &le;&nbsp;<em>n</em>&nbsp;&le; 30），输出报数序列的第 <em>n</em> 项。</p>

<p>注意：整数顺序将表示为一个字符串。</p>

<p>&nbsp;</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> 1
<strong>输出:</strong> &quot;1&quot;
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 4
<strong>输出:</strong> &quot;1211&quot;
</pre>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/count-and-say/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/count-and-say/description/)

## 题解

这题用到了字符串压缩的思想，即把aaabb压缩成3a2b这种由数量与字符构成的字符串。基本做法是：pre保存前一个字符，cnt保存字符计数，遇到和pre相同就把cnt=1，不同就拼接到结果字符串，然后把pre设为当前字符，cnt=1，如此遍历；循环结束再做一次拼接到结果字符串。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 60  ms | N/A |

```python3
class Solution:
    dp = {1: '1'}
    def countAndSay(self, n):
        """
        :type n: int
        :rtype: str
        """
        if n in self.__class__.dp:
            return self.__class__.dp[n]
        else:
            for i in range(int(max(self.__class__.dp)), n+1):
                cnt, pre = 1, self.__class__.dp[i][0]
                tmp = ''
                for ii in self.__class__.dp[i][1:]:
                    if pre:
                        if pre == ii:
                            cnt += 1
                        else:
                            tmp += str(cnt) + pre
                            pre = ii
                            cnt = 1
                tmp += str(cnt) + pre
                self.__class__.dp[i+1] = tmp
            return self.__class__.dp[n]
```
