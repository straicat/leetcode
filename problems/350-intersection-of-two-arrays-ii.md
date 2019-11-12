## 350. Intersection of Two Arrays II - 两个数组的交集 II

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个数组，编写一个函数来计算它们的交集。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>nums1 = [1,2,2,1], nums2 = [2,2]
<strong>输出: </strong>[2,2]
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>nums1 = [4,9,5], nums2 = [9,4,9,8,4]
<strong>输出: </strong>[4,9]</pre>

<p><strong>说明：</strong></p>

<ul>
	<li>输出结果中每个元素出现的次数，应与元素在两个数组中出现的次数一致。</li>
	<li>我们可以不考虑输出结果的顺序。</li>
</ul>

<p><strong><strong>进阶:</strong></strong></p>

<ul>
	<li>如果给定的数组已经排好序呢？你将如何优化你的算法？</li>
	<li>如果&nbsp;<em>nums1&nbsp;</em>的大小比&nbsp;<em>nums2&nbsp;</em>小很多，哪种方法更优？</li>
	<li>如果&nbsp;<em>nums2&nbsp;</em>的元素存储在磁盘上，磁盘内存是有限的，并且你不能一次加载所有的元素到内存中，你该怎么办？</li>
</ul>



-----

题目标签：Sort / Hash Table / Two Pointers / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/intersection-of-two-arrays-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/intersection-of-two-arrays-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python  | 112  ms | N/A |

```python
class Solution(object):
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        tmp = []
        for a in nums1:
            for b in nums2:
                if a == b:
                    nums2.remove(b)
                    tmp.append(a)
                    break
        return tmp
```
