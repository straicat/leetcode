## 169. Majority Element - 求众数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个大小为 <em>n </em>的数组，找到其中的众数。众数是指在数组中出现次数<strong>大于</strong>&nbsp;<code>&lfloor; n/2 &rfloor;</code>&nbsp;的元素。</p>

<p>你可以假设数组是非空的，并且给定的数组总是存在众数。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [3,2,3]
<strong>输出:</strong> 3</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [2,2,1,1,1,2,2]
<strong>输出:</strong> 2
</pre>



-----

题目标签：Bit Manipulation / Array / Divide and Conquer

题目链接：[LeetCode](https://leetcode.com/problems/majority-element/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/majority-element/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 2.8 MB |

```cpp
// Boyer-Moore Majority Vote Algorithm
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int n = 0, c = 0;
        for (int i : nums) {
            if (i == c) {
                n++;
            } else if (n == 0) {
                c = i;
                n = 1;
            } else {
                n--;
            }
        }
        return c;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 52  ms | N/A |

```python3
class Solution:
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return sorted([(k, v) for k, v in collections.Counter(nums).items()], key=lambda x: x[1], reverse=True)[0][0]
```
