## 665. Non-decreasing Array - 非递减数列

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个长度为&nbsp;<code>n</code>&nbsp;的整数数组，你的任务是判断在<strong>最多</strong>改变&nbsp;<code>1</code> 个元素的情况下，该数组能否变成一个非递减数列。</p>

<p>我们是这样定义一个非递减数列的：&nbsp;对于数组中所有的&nbsp;<code>i</code> (1 &lt;= i &lt; n)，满足&nbsp;<code>array[i] &lt;= array[i + 1]</code>。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [4,2,3]
<strong>输出:</strong> True
<strong>解释:</strong> 你可以通过把第一个4变成1来使得它成为一个非递减数列。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> [4,2,1]
<strong>输出:</strong> False
<strong>解释:</strong> 你不能在只改变一个元素的情况下将其变为非递减数列。
</pre>

<p><strong>说明:&nbsp;&nbsp;</strong><code>n</code> 的范围为 [1, 10,000]。</p>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/non-decreasing-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/non-decreasing-array/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 72  ms | N/A |

```python3
class Solution:
    def checkPossibility(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        '''
        Testcase
        [3,4,2,3]
        [2,3,3,2,4]
        [2,9,3,5]
        '''
        if len(nums) < 3:
            return True
        tmp = list(nums)
        flag = False
        for i in range(1, len(tmp)-1):
            a, b, c = tmp[i-1], tmp[i], tmp[i+1]
            if a <= b <= c:
                continue
            else:
                if a > b > c:
                    return False
                if flag:
                    return False
                else:
                    flag = True
                    if a == c and b < a:
                        tmp[i] = a
                    elif a == b and c < a:
                        tmp[i+1] = a
                    elif b > c > a or c > a > b:
                        tmp[i] = a
                    elif b > a > c:
                        tmp[i+1] = b
                    elif a > c > b:
                        tmp[i-1] = b
        return True
```
