## 41. First Missing Positive - 缺失的第一个正数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个未排序的整数数组，找出其中没有出现的最小的正整数。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>输入: [1,2,0]
输出: 3
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre>输入: [3,4,-1,1]
输出: 2
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre>输入: [7,8,9,11,12]
输出: 1
</pre>

<p><strong>说明:</strong></p>

<p>你的算法的时间复杂度应为O(<em>n</em>)，并且只能使用常数级别的空间。</p>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/first-missing-positive/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/first-missing-positive/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 9 MB |

```cpp
// 左程云《程序员代码面试指南》：数组中未出现的最小正整数
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int l = 0, r = nums.size();
        while (l < r) {
            if (nums[l] == l + 1) {
                l++;
            } else if (nums[l] <= l || nums[l] > r || nums[l] == nums[nums[l] - 1]) {
                nums[l] = nums[--r];
            } else {
                swap(nums[l], nums[nums[l] - 1]);
            }
        }
        return l + 1;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 0  ms | 36.8 MB |

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int p = 0;
        while (p < nums.length) {
            if (nums[p] <= 0 || nums[p] == p + 1) {
                p++;
            } else {
                if (nums[p] > nums.length) {
                    nums[p++] = -1;
                } else {
                    int tmp = nums[nums[p] - 1];
                    if (tmp == nums[p]) {
                        nums[p++] = -1;
                    } else {
                        nums[nums[p] - 1] = nums[p];
                        nums[p] = tmp;
                    }
                }
            }
        }
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] <= 0) return i + 1;
        }
        return nums.length + 1;
    }
}
```
