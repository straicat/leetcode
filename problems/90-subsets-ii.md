## 90. Subsets II - 子集 II

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个可能包含重复元素的整数数组 <em><strong>nums</strong></em>，返回该数组所有可能的子集（幂集）。</p>

<p><strong>说明：</strong>解集不能包含重复的子集。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,2,2]
<strong>输出:</strong>
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]</pre>



-----

题目标签：Array / Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/subsets-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/subsets-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 1.1 MB |

```cpp
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        set<vector<int> > us;
        vector<vector<int> > res;
        vector<int> tmp;
        for (int i=0; i<pow(2, nums.size()); ++i) {
            tmp.clear();
            for (int j=0; j<(int)nums.size(); ++j) {
                if (1 & (i >> j)) {
                    tmp.push_back(nums[j]);
                }
            }
            if (!us.count(tmp)) {
                res.push_back(tmp);
                us.insert(tmp);
            }
        }
        return res;
    }
};
```
