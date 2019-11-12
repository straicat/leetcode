## 215. Kth Largest Element in an Array - 数组中的第K个最大元素

<!--If you want to use the English description, use `question.content` instead-->

<p>在未排序的数组中找到第 <strong>k</strong> 个最大的元素。请注意，你需要找的是数组排序后的第 k 个最大的元素，而不是第 k 个不同的元素。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <code>[3,2,1,5,6,4] 和</code> k = 2
<strong>输出:</strong> 5
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> <code>[3,2,3,1,2,4,5,5,6] 和</code> k = 4
<strong>输出:</strong> 4</pre>

<p><strong>说明: </strong></p>

<p>你可以假设 k 总是有效的，且 1 &le; k &le; 数组的长度。</p>



-----

题目标签：Heap / Divide and Conquer

题目链接：[LeetCode](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 33  ms | 36.3 MB |

```java
class Solution {
    public int partition(int[] nums, int k, int st, int ed) {
        if (st > ed || k > nums.length) return -1;

        int left = st;
        int right = ed;
        int pivot = st;
        
        while (left < right) {
            while (left < right && nums[right] <= nums[pivot]) 
                right--;
            while (left < right && nums[left] >= nums[pivot])
                left++;
            if (left < right) {
                int tmp = nums[left];
                nums[left] = nums[right];
                nums[right] = tmp;
            }
        }
        int tmp = nums[left];
        nums[left] = nums[pivot];
        nums[pivot] = tmp;

        if (left > k - 1) {
            partition(nums, k, st, left - 1);
        }
        if (left < k - 1) {
            partition(nums, k, left + 1, ed);
        }
        return nums[k - 1];
    }
    
    public int findKthLargest(int[] nums, int k) {
        return partition(nums, k, 0, nums.length - 1);
    }
}
```
