## 258. Add Digits - 各位相加

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非负整数 <code>num</code>，反复将各个位上的数字相加，直到结果为一位数。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> <code>38</code>
<strong>输出:</strong> 2 
<strong>解释: </strong>各位相加的过程为<strong>：</strong><code>3 + 8 = 11</code>, <code>1 + 1 = 2</code>。 由于&nbsp;<code>2</code> 是一位数，所以返回 2。
</pre>

<p><strong>进阶:</strong><br>
你可以不使用循环或者递归，且在 O(1) 时间复杂度内解决这个问题吗？</p>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/add-digits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-digits/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 76  ms | N/A |

```python3
class Solution:
    def addDigits(self, num):
        """
        :type num: int
        :rtype: int
        """
        if num < 10:
            return num
        else:
            return self.addDigits(sum(map(int, str(num))))
```
