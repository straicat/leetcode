## 349. Intersection of Two Arrays - 两个数组的交集

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个数组，编写一个函数来计算它们的交集。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>nums1 = [1,2,2,1], nums2 = [2,2]
<strong>输出: </strong>[2]
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>nums1 = [4,9,5], nums2 = [9,4,9,8,4]
<strong>输出: </strong>[9,4]</pre>

<p><strong>说明:</strong></p>

<ul>
	<li>输出结果中的每个元素一定是唯一的。</li>
	<li>我们可以不考虑输出结果的顺序。</li>
</ul>



-----

题目标签：Sort / Hash Table / Two Pointers / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/intersection-of-two-arrays/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/intersection-of-two-arrays/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| ruby  | 84  ms | N/A |

```ruby
# @param {Integer[]} nums1
# @param {Integer[]} nums2
# @return {Integer[]}
def intersection(nums1, nums2)
    nums1 & nums2
end
```
