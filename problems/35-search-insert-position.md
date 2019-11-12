## 35. Search Insert Position - 搜索插入位置

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。</p>

<p>你可以假设数组中无重复元素。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,3,5,6], 5
<strong>输出:</strong> 2
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [1,3,5,6], 2
<strong>输出:</strong> 1
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> [1,3,5,6], 7
<strong>输出:</strong> 4
</pre>

<p><strong>示例 4:</strong></p>

<pre><strong>输入:</strong> [1,3,5,6], 0
<strong>输出:</strong> 0
</pre>



-----

题目标签：Array / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/search-insert-position/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-insert-position/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| c  | 3  ms | N/A |

```c
int searchInsert(int* nums, int numsSize, int target) {
    int pos = 0;
    for (int i = 0; i < numsSize; i++) {
        if (*(nums + i) == target) {
            return i;
        }
        if (*(nums + i) < target) {
            pos = i + 1;
        }
    }
    return pos;
}
```
