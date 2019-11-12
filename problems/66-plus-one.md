## 66. Plus One - 加一

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个由<strong>整数</strong>组成的<strong>非空</strong>数组所表示的非负整数，在该数的基础上加一。</p>

<p>最高位数字存放在数组的首位， 数组中每个元素只存储<strong>单个</strong>数字。</p>

<p>你可以假设除了整数 0 之外，这个整数不会以零开头。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [1,2,3]
<strong>输出:</strong> [1,2,4]
<strong>解释:</strong> 输入数组表示数字 123。
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [4,3,2,1]
<strong>输出:</strong> [4,3,2,2]
<strong>解释:</strong> 输入数组表示数字 4321。
</pre>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/plus-one/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/plus-one/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 48  ms | N/A |

```python3
class Solution:
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        res = list(digits)
        res[-1] += 1
        for i in range(len(res)-1, -1, -1):
            a, b = res[i] // 10, res[i] % 10
            res[i] = b
            if a == 0:
                break
            else:
                if i == 0:
                    res.insert(0, a)
                else:
                    res[i-1] += a
        return res
```
