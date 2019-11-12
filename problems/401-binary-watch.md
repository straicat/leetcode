## 401. Binary Watch - 二进制手表

<!--If you want to use the English description, use `question.content` instead-->

<p>二进制手表顶部有 4 个 LED 代表<strong>小时（0-11）</strong>，底部的 6 个 LED 代表<strong>分钟（0-59）</strong>。</p>

<p>每个 LED 代表一个 0 或 1，最低位在右侧。</p>

<p><img src="https://upload.wikimedia.org/wikipedia/commons/8/8b/Binary_clock_samui_moon.jpg" style="height:300px" /></p>

<p>例如，上面的二进制手表读取 &ldquo;3:25&rdquo;。</p>

<p>给定一个非负整数 <em>n&nbsp;</em>代表当前 LED 亮着的数量，返回所有可能的时间。</p>

<p><strong>案例:</strong></p>

<pre>
输入: n = 1
返回: [&quot;1:00&quot;, &quot;2:00&quot;, &quot;4:00&quot;, &quot;8:00&quot;, &quot;0:01&quot;, &quot;0:02&quot;, &quot;0:04&quot;, &quot;0:08&quot;, &quot;0:16&quot;, &quot;0:32&quot;]</pre>

<p>&nbsp;</p>

<p><strong>注意事项:</strong></p>

<ul>
	<li>输出的顺序没有要求。</li>
	<li>小时不会以零开头，比如 &ldquo;01:00&rdquo;&nbsp;是不允许的，应为 &ldquo;1:00&rdquo;。</li>
	<li>分钟必须由两位数组成，可能会以零开头，比如 &ldquo;10:2&rdquo;&nbsp;是无效的，应为 &ldquo;10:02&rdquo;。</li>
</ul>



-----

题目标签：Bit Manipulation / Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/binary-watch/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-watch/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 56  ms | 6.5 MB |

```python3
class Solution:
    def readHour(self, num):
        res = []
        for i in range(12):
            if bin(i).count('1') == num:
                res.append(str(i))
        return res
    
    def readMinute(self, num):
        res = []
        for i in range(60):
            if bin(i).count('1') == num:
                res.append(str(i).rjust(2, '0'))
        return res

    def readBinaryWatch(self, num):
        """
        :type num: int
        :rtype: List[str]
        """
        res = []
        for i in range(num + 1):
            a = self.readHour(i)
            b = self.readMinute(num - i)
            if a and b:
                for ai in a:
                    for bi in b:
                        res.append('%s:%s' % (ai, bi))
        return res
```
