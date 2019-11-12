## 378. Kth Smallest Element in a Sorted Matrix - 有序矩阵中第K小的元素

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个&nbsp;<em>n x n&nbsp;</em>矩阵，其中每行和每列元素均按升序排序，找到矩阵中第k小的元素。<br />
请注意，它是排序后的第k小元素，而不是第k个元素。</p>

<p><strong>示例:</strong></p>

<pre>
matrix = [
   [ 1,  5,  9],
   [10, 11, 13],
   [12, 13, 15]
],
k = 8,

返回 13。
</pre>

<p><strong>说明: </strong><br />
你可以假设 k 的值永远是有效的, 1 &le; k &le; n<sup>2&nbsp;</sup>。</p>



-----

题目标签：Heap / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/kth-smallest-element-in-a-sorted-matrix/description/)

## 题解

用ruby解这题感觉有点不讲道理。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| ruby  | 76  ms | N/A |

```ruby
# @param {Integer[][]} matrix
# @param {Integer} k
# @return {Integer}
def kth_smallest(matrix, k)
    matrix.flatten.sort.at(k-1)
end
```
