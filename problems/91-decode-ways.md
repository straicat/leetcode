## 91. Decode Ways - 解码方法

<!--If you want to use the English description, use `question.content` instead-->

<p>一条包含字母&nbsp;<code>A-Z</code> 的消息通过以下方式进行了编码：</p>

<pre>&#39;A&#39; -&gt; 1
&#39;B&#39; -&gt; 2
...
&#39;Z&#39; -&gt; 26
</pre>

<p>给定一个只包含数字的<strong>非空</strong>字符串，请计算解码方法的总数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> &quot;12&quot;
<strong>输出:</strong> 2
<strong>解释:</strong>&nbsp;它可以解码为 &quot;AB&quot;（1 2）或者 &quot;L&quot;（12）。
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> &quot;226&quot;
<strong>输出:</strong> 3
<strong>解释:</strong>&nbsp;它可以解码为 &quot;BZ&quot; (2 26), &quot;VF&quot; (22 6), 或者 &quot;BBF&quot; (2 2 6) 。
</pre>



-----

题目标签：String / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/decode-ways/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/decode-ways/description/)

## 题解

题目不难，就是不容易考虑周全。

对于长度为2的字符串，如果以0开头，有0种编码；如果以0结尾，只有10、20有1种编码，其余有0种编码；剩下的当不大于26时有2种编码，否则只有1种编码。

递推关系：

F(s) = g(s[:1])F(s[1:]) + g(s[:2])F(s[2:])

其中g表示是否存在编码。

然后可以采用记忆化搜索或动态规划求解。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 52  ms | N/A |

```python3
class Solution:
    cache = {}
    def numDecodings(self, s):
        """
        :type s: str
        :rtype: int
        """
        if len(s) == 0:
            return 0
        elif len(s) == 1:
            return int(int(s) > 0)
        elif len(s) == 2:
            if s.startswith('0') or (s.endswith('0') and int(s[0]) > 2):
                return 0
            else:
                return 1 + int(int(s) <= 26 and not s.endswith('0'))
        else:
            if s in __class__.cache:
                return __class__.cache[s]
            else:
                res = 0
                if int(s[:1]) > 0:
                    res += self.numDecodings(s[1:])
                if 10 <= int(s[:2]) <= 26:
                    res += self.numDecodings(s[2:])
                __class__.cache[s] = res
                return res
```
