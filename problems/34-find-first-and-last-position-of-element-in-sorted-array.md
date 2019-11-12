## 34. Find First and Last Position of Element in Sorted Array - 在排序数组中查找元素的第一个和最后一个位置

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个按照升序排列的整数数组 <code>nums</code>，和一个目标值 <code>target</code>。找出给定目标值在数组中的开始位置和结束位置。</p>

<p>你的算法时间复杂度必须是&nbsp;<em>O</em>(log <em>n</em>) 级别。</p>

<p>如果数组中不存在目标值，返回&nbsp;<code>[-1, -1]</code>。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> nums = [<code>5,7,7,8,8,10]</code>, target = 8
<strong>输出:</strong> [3,4]</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> nums = [<code>5,7,7,8,8,10]</code>, target = 6
<strong>输出:</strong> [-1,-1]</pre>



-----

题目标签：Array / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/)

## 题解

考查二分法及其变体。

二分法比较简单，然而，并不容易写对。主要是下标越界、死循环、是否取等号、+1 -1、变left还是right等问题。。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 0  ms | 44.4 MB |

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        if (nums.length == 0) return new int[]{-1, -1};
        int left = 0, right = nums.length - 1;
        while (left < right) {
            int mid = left + right >> 1;
            if (nums[mid] >= target) right = mid;
            else left = mid + 1;
        }
        if (nums[left] != target) return new int[]{-1, -1};
        int st = left;
        left = st; right = nums.length - 1;
        while (left < right) {
            int mid = left + right + 1 >> 1;
            if (nums[mid] <= target) left = mid;
            else right = mid - 1;
        }
        return new int[]{st, left};
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 12  ms | N/A |

```cpp
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        int left = 0, right = nums.size() - 1;
        while(left <= right){
            int mid = (left + right) / 2;
            if(nums.at(mid) == target){
                int lleft = left, lright = right;
                while(lleft <= lright){
                    int lmid = (lleft + lright) / 2;
                    if(nums.at(lmid) >= target){
                        lright = lmid - 1;
                    }else{
                        lleft = lmid + 1;
                    }
                }
                int rleft = left, rright = right;
                while(rleft <= rright){
                    int rmid = (rleft + rright) / 2;
                    if(nums.at(rmid) > target){
                        rright = rmid - 1;
                    }else{
                        rleft = rmid + 1;
                    }
                }
                return vector<int>{lleft, rright};
            }else if(nums.at(mid) > target){
                right = mid - 1;
            }else{
                left = mid + 1;
            }
        }
        return vector<int>{-1, -1};
    }
};
```
