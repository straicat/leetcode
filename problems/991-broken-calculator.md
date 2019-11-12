## 991. Broken Calculator - 坏了的计算器

<!--If you want to use the English description, use `question.content` instead-->

<p>在显示着数字的坏计算器上，我们可以执行以下两种操作：</p>

<ul>
	<li><strong>双倍（Double）：</strong>将显示屏上的数字乘 2；</li>
	<li><strong>递减（Decrement）：</strong>将显示屏上的数字减 1 。</li>
</ul>

<p>最初，计算器显示数字&nbsp;<code>X</code>。</p>

<p>返回显示数字&nbsp;<code>Y</code>&nbsp;所需的最小操作数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>X = 2, Y = 3
<strong>输出：</strong>2
<strong>解释：</strong>先进行双倍运算，然后再进行递减运算 {2 -&gt; 4 -&gt; 3}.
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>X = 5, Y = 8
<strong>输出：</strong>2
<strong>解释：</strong>先递减，再双倍 {5 -&gt; 4 -&gt; 8}.
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>X = 3, Y = 10
<strong>输出：</strong>3
<strong>解释：</strong>先双倍，然后递减，再双倍 {3 -&gt; 6 -&gt; 5 -&gt; 10}.
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>X = 1024, Y = 1
<strong>输出：</strong>1023
<strong>解释：</strong>执行递减运算 1023 次
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= X &lt;= 10^9</code></li>
	<li><code>1 &lt;= Y &lt;= 10^9</code></li>
</ol>



-----

题目标签：Greedy / Math

题目链接：[LeetCode](https://leetcode.com/problems/broken-calculator/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/broken-calculator/description/)

## 题解

![image](https://user-images.githubusercontent.com/9983385/54613805-4f730a80-4a96-11e9-83aa-050014bf98ff.png)



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 8.5 MB |

```cpp
class Solution {
public:
    int brokenCalc(int X, int Y) {
        if (X >= Y) {
            return X - Y;
        } else {
            if (Y & 1) {
                return brokenCalc(X, Y + 1) + 1;
            } else {
                return brokenCalc(X, Y / 2) + 1;
            }
        }
    }
};
```
