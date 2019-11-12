## 229. Majority Element II - 求众数 II

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个大小为&nbsp;<em>n&nbsp;</em>的数组，找出其中所有出现超过&nbsp;<code>&lfloor; n/3 &rfloor;</code>&nbsp;次的元素。</p>

<p><strong>说明: </strong>要求算法的时间复杂度为 O(n)，空间复杂度为 O(1)。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [3,2,3]
<strong>输出:</strong> [3]</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [1,1,1,3,3,2,2,2]
<strong>输出:</strong> [1,2]</pre>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/majority-element-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/majority-element-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 2.5 MB |

```cpp
// Boyer-Moore Majority Vote  Algorithm
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        vector<int> res;
        if (nums.empty()) return res;
        if (nums.size() < 2) {
            res.push_back(nums[0]);
            return res;
        }
        int n1 = 0, n2 = 0, c1 = 0, c2 = 1;
        for (int i = 0; i < nums.size(); ++i) {
            int n = nums[i];
            if (n == c1) {
                n1++;
            } else if (n == c2) {
                n2++;
            } else if (n1 == 0) {
                c1 = n;
                n1 = 1;
            } else if (n2 == 0) {
                c2 = n;
                n2 = 1;
            } else {
                n1--;
                n2--;
            }
        }
        n1 = 0, n2 = 0;
        for (int n : nums) {
            if (n == c1) {
                n1++;
            } else if (n == c2) {
                n2++;
            }
        }
        if (n1 > nums.size() / 3) {
            res.push_back(c1);
        }
        if (n2 > nums.size() / 3) {
            res.push_back(c2);
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
