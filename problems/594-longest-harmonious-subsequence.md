## 594. Longest Harmonious Subsequence - 最长和谐子序列

<!--If you want to use the English description, use `question.content` instead-->

<p>和谐数组是指一个数组里元素的最大值和最小值之间的差别正好是1。</p>

<p>现在，给定一个整数数组，你需要在所有可能的子序列中找到最长的和谐子序列的长度。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [1,3,2,2,5,2,3,7]
<strong>输出:</strong> 5
<strong>原因:</strong> 最长的和谐数组是：[3,2,2,2,3].
</pre>

<p><strong>说明:</strong> 输入的数组长度最大不超过20,000.</p>



-----

题目标签：Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/longest-harmonious-subsequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-harmonious-subsequence/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 148  ms | N/A |

```python3
class Solution:
    def findLHS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        res = 0
        cnt = sorted(list(collections.Counter(nums).items()), key=lambda x: x[0])
        for i in range(len(cnt)-1):
            if abs(cnt[i][0] - cnt[i+1][0]) == 1:
                res = max(res, cnt[i][1] + cnt[i+1][1])
        return res
```
