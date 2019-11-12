## 33. Search in Rotated Sorted Array - 搜索旋转排序数组

<!--If you want to use the English description, use `question.content` instead-->

<p>假设按照升序排序的数组在预先未知的某个点上进行了旋转。</p>

<p>( 例如，数组&nbsp;<code>[0,1,2,4,5,6,7]</code>&nbsp;可能变为&nbsp;<code>[4,5,6,7,0,1,2]</code>&nbsp;)。</p>

<p>搜索一个给定的目标值，如果数组中存在这个目标值，则返回它的索引，否则返回&nbsp;<code>-1</code>&nbsp;。</p>

<p>你可以假设数组中不存在重复的元素。</p>

<p>你的算法时间复杂度必须是&nbsp;<em>O</em>(log&nbsp;<em>n</em>) 级别。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> nums = [<code>4,5,6,7,0,1,2]</code>, target = 0
<strong>输出:</strong> 4
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> nums = [<code>4,5,6,7,0,1,2]</code>, target = 3
<strong>输出:</strong> -1</pre>



-----

题目标签：Array / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 12  ms | 8.6 MB |

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        if (nums.empty()) return -1;
        int l = 0;
        int r = (int)nums.size() - 1;
        if (nums[0] < nums[(int)nums.size() - 1]) {
            while (l <= r) {
                int mid = l + r >> 1;
                if (nums[mid] == target) return mid;
                if (nums[mid] > target) r = mid - 1;
                else l = mid + 1;
            }
            return -1;
        }
        while (l < r) {
            if (target >= nums[0]) {
                int mid = l + r >> 1;
                if (nums[mid] >= target) r = mid;
                else {
                    if (nums[mid] >= nums[0]) l = mid + 1;
                    else r = mid - 1;
                }
            } else {
                int mid = l + r + 1 >> 1;
                if (nums[mid] <= target) l = mid;
                else {
                    if (nums[mid] >= nums[0]) l = mid + 1;
                    else r = mid - 1;
                }
            }
        }
        return nums[l] == target ? l : -1;
    }
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 52  ms | N/A |

```python3
class Solution:
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        return nums.index(target) if target in nums else -1
```
