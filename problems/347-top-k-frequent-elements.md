## 347. Top K Frequent Elements - 前 K 个高频元素

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非空的整数数组，返回其中出现频率前&nbsp;<strong><em>k&nbsp;</em></strong>高的元素。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>nums = [1,1,1,2,2,3], k = 2
<strong>输出: </strong>[1,2]
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>nums = [1], k = 1
<strong>输出: </strong>[1]</pre>

<p><strong>说明：</strong></p>

<ul>
	<li>你可以假设给定的&nbsp;<em>k&nbsp;</em>总是合理的，且 1 &le; k &le; 数组中不相同的元素的个数。</li>
	<li>你的算法的时间复杂度<strong>必须</strong>优于 O(<em>n</em> log <em>n</em>) ,&nbsp;<em>n&nbsp;</em>是数组的大小。</li>
</ul>



-----

题目标签：Heap / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/top-k-frequent-elements/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/top-k-frequent-elements/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 48  ms | N/A |

```python3
class Solution:
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        return [r[0] for r in sorted(list(collections.Counter(nums).items()), key=lambda x: -x[1])[:k]]
```
