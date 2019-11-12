## 503. Next Greater Element II - 下一个更大元素 II

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个循环数组（最后一个元素的下一个元素是数组的第一个元素），输出每个元素的下一个更大元素。数字 x 的下一个更大的元素是按数组遍历顺序，这个数字之后的第一个比它更大的数，这意味着你应该循环地搜索它的下一个更大的数。如果不存在，则输出 -1。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1,2,1]
<strong>输出:</strong> [2,-1,2]
<strong>解释:</strong> 第一个 1 的下一个更大的数是 2；
数字 2 找不到下一个更大的数； 
第二个 1 的下一个最大的数需要循环搜索，结果也是 2。
</pre>

<p><strong>注意:</strong> 输入数组的长度不会超过 10000。</p>



-----

题目标签：Stack

题目链接：[LeetCode](https://leetcode.com/problems/next-greater-element-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/next-greater-element-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 216  ms | 15.5 MB |

```python3
class Solution:
    def nextGreaterElements(self, nums: List[int]) -> List[int]:
        lnums = nums + nums
        stk = []
        ret = [-1] * len(lnums)
        for i, num in enumerate(lnums):
            while stk and num > stk[-1][1]:
                ret[stk.pop()[0]] = num
            stk.append((i, num))
        res = []
        for i in range(len(nums)):
            t = [ret[i], ret[i + len(nums)]]
            if -1 in t:
                t.remove(-1)
            if t:
                res.append(min(t))
            else:
                res.append(-1)
        return res
```
