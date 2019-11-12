## 728. Self Dividing Numbers - 自除数

<!--If you want to use the English description, use `question.content` instead-->

<p><em>自除数&nbsp;</em>是指可以被它包含的每一位数除尽的数。</p>

<p>例如，128 是一个自除数，因为&nbsp;<code>128 % 1 == 0</code>，<code>128 % 2 == 0</code>，<code>128 % 8 == 0</code>。</p>

<p>还有，自除数不允许包含 0 。</p>

<p>给定上边界和下边界数字，输出一个列表，列表的元素是边界（含边界）内所有的自除数。</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong> 
上边界left = 1, 下边界right = 22
<strong>输出：</strong> [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]
</pre>

<p><strong>注意：</strong></p>

<ul>
	<li>每个输入参数的边界满足&nbsp;<code>1 &lt;= left &lt;= right &lt;= 10000</code>。</li>
</ul>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/self-dividing-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/self-dividing-numbers/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 92  ms | N/A |

```python3
class Solution:
    def selfDividingNumbers(self, left, right):
        """
        :type left: int
        :type right: int
        :rtype: List[int]
        """
        res = []
        for num in range(left, right+1):
            snum = str(num)
            if '0' in snum:
                continue
            for i in snum:
                if num % int(i) != 0:
                    break
            else:
                res.append(num)
        return res
```
