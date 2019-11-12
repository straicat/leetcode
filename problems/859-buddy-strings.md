## 859. Buddy Strings - 亲密字符串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个由小写字母构成的字符串&nbsp;<code>A</code>&nbsp;和&nbsp;<code>B</code>&nbsp;，只要我们可以通过交换 <code>A</code> 中的两个字母得到与 <code>B</code> 相等的结果，就返回&nbsp;<code>true</code>&nbsp;；否则返回 <code>false</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入： </strong>A = &quot;ab&quot;, B = &quot;ba&quot;
<strong>输出： </strong>true
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入： </strong>A = &quot;ab&quot;, B = &quot;ab&quot;
<strong>输出： </strong>false
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入： </strong>A = &quot;aa&quot;, B = &quot;aa&quot;
<strong>输出： </strong>true
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入： </strong>A = &quot;aaaaaaabc&quot;, B = &quot;aaaaaaacb&quot;
<strong>输出： </strong>true
</pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入： </strong>A = &quot;&quot;, B = &quot;aa&quot;
<strong>输出： </strong>false
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>0 &lt;= A.length &lt;= 20000</code></li>
	<li><code>0 &lt;= B.length &lt;= 20000</code></li>
	<li><code>A</code>&nbsp;和&nbsp;<code>B</code>&nbsp;仅由小写字母构成。</li>
</ol>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/buddy-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/buddy-strings/description/)

## 题解

这题似乎在答笔试时做过，当时一次性AC，现在却错了好几次，主要是考虑不周全。

如果交换字符串A中两个字符能得到字符串B，则A和B是亲密字符串。

1、如果A和B长度不等，那么必然不是亲密字符串

2、如果A和B长度相等，那么分A和B是否相同两种情况

3、如果A和B相同，要成为亲密字符串，那么只能交换两个相同的字符，因此就进行字符计数，如果有字符出现了两次及以上，那么就是A和B就是亲密字符串，否则就不是。

4、如果A和B长度相同且是不同的字符串，就要用双指针遍历A和B。这里主要需要注意两点：(1)当出现了两处不同且不同之处对称时，不能立即给出判断，还要看后面还有没有不同的；当然，如果有3处不同那么就肯定不是亲密字符串了，如果前面两处不同之处不对称也肯定不是亲密字符串了 (2)由于遇到两处对称不同后不能立即给出判断，因此，在循环结束时要再返回下判断结果，如果前面在3处不同时或前面两处不同不对称时立即返回False，那么这里可以直接返回True，否则就要判断下是否有且仅有两处不同且对称。



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 32  ms | N/A |

```python3
class Solution:
    def buddyStrings(self, A, B):
        """
        :type A: str
        :type B: str
        :rtype: bool
        """
        if len(A) == len(B):
            if A == B:
                for v in collections.Counter(A).values():
                    if v > 1:
                        return True
                return False
            else:
                tmp = ''
                for i in range(len(A)):
                    x, y = A[i], B[i]
                    if x != y:
                        if tmp:
                            if tmp == y + x:
                                tmp += y + x
                            else:
                                return False
                        else:
                            tmp = x + y
                return True
        else:
            return False
```
