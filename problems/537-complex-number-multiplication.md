## 537. Complex Number Multiplication - 复数乘法

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个表示<a href="https://baike.baidu.com/item/%E5%A4%8D%E6%95%B0/254365?fr=aladdin">复数</a>的字符串。</p>

<p>返回表示它们乘积的字符串。注意，根据定义 i<sup>2</sup> = -1 。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> &quot;1+1i&quot;, &quot;1+1i&quot;
<strong>输出:</strong> &quot;0+2i&quot;
<strong>解释:</strong> (1 + i) * (1 + i) = 1 + i<sup>2</sup> + 2 * i = 2i ，你需要将它转换为 0+2i 的形式。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> &quot;1+-1i&quot;, &quot;1+-1i&quot;
<strong>输出:</strong> &quot;0+-2i&quot;
<strong>解释:</strong> (1 - i) * (1 - i) = 1 + i<sup>2</sup> - 2 * i = -2i ，你需要将它转换为 0+-2i 的形式。 
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>输入字符串不包含额外的空格。</li>
	<li>输入字符串将以&nbsp;<strong>a+bi</strong> 的形式给出，其中整数 <strong>a</strong> 和 <strong>b</strong> 的范围均在 [-100, 100] 之间。<strong>输出也应当符合这种形式</strong>。</li>
</ol>



-----

题目标签：Math / String

题目链接：[LeetCode](https://leetcode.com/problems/complex-number-multiplication/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/complex-number-multiplication/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 56  ms | N/A |

```python3
class Solution:
    def complexNumberMultiply(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        a1, b1 = map(int, a[:-1].split('+'))
        a2, b2 = map(int, b[:-1].split('+'))
        return '%d+%di' % (a1*a2-b1*b2, a1*b2+a2*b1)
```
