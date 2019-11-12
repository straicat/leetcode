## 925. Long Pressed Name - 长按键入

<!--If you want to use the English description, use `question.content` instead-->

<p>你的朋友正在使用键盘输入他的名字&nbsp;<code>name</code>。偶尔，在键入字符&nbsp;<code>c</code>&nbsp;时，按键可能会被<em>长按</em>，而字符可能被输入 1 次或多次。</p>

<p>你将会检查键盘输入的字符&nbsp;<code>typed</code>。如果它对应的可能是你的朋友的名字（其中一些字符可能被长按），那么就返回&nbsp;<code>True</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>name = &quot;alex&quot;, typed = &quot;aaleex&quot;
<strong>输出：</strong>true
<strong>解释：</strong>&#39;alex&#39; 中的 &#39;a&#39; 和 &#39;e&#39; 被长按。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>name = &quot;saeed&quot;, typed = &quot;ssaaedd&quot;
<strong>输出：</strong>false
<strong>解释：</strong>&#39;e&#39; 一定需要被键入两次，但在 typed 的输出中不是这样。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>name = &quot;leelee&quot;, typed = &quot;lleeelee&quot;
<strong>输出：</strong>true
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>name = &quot;laiden&quot;, typed = &quot;laiden&quot;
<strong>输出：</strong>true
<strong>解释：</strong>长按名字中的字符并不是必要的。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>name.length &lt;= 1000</code></li>
	<li><code>typed.length &lt;= 1000</code></li>
	<li><code>name</code> 和&nbsp;<code>typed</code>&nbsp;的字符都是小写字母。</li>
</ol>

<p>&nbsp;</p>

<p>&nbsp;</p>



-----

题目标签：Two Pointers / String

题目链接：[LeetCode](https://leetcode.com/problems/long-pressed-name/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/long-pressed-name/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 124  ms | N/A |

```python3
import re
class Solution:
    def isLongPressedName(self, name, typed):
        """
        :type name: str
        :type typed: str
        :rtype: bool
        """
        if name == typed:
            return True
        if len(typed) < len(name):
            return False
        r = ''
        for c in name:
            r += c + '+'
        return bool(re.fullmatch(r, typed))
```
