## 78. Subsets - 子集

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一组<strong>不含重复元素</strong>的整数数组&nbsp;<em>nums</em>，返回该数组所有可能的子集（幂集）。</p>

<p><strong>说明：</strong>解集不能包含重复的子集。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> nums = [1,2,3]
<strong>输出:</strong>
[
  [3],
&nbsp; [1],
&nbsp; [2],
&nbsp; [1,2,3],
&nbsp; [1,3],
&nbsp; [2,3],
&nbsp; [1,2],
&nbsp; []
]</pre>



-----

题目标签：Bit Manipulation / Array / Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/subsets/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/subsets/description/)

## 题解

递归就像机器人造小机器人帮自己干活，注意递归终止条件。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | N/A |

```cpp
class Solution {
private:
    void robot(int idx, vector<int>& nums, vector<vector<int>>& res, vector<bool>& mask){
        if(idx >= nums.size()){
            vector<int> r;
            for(int i=0; i<nums.size(); i++){
                if(mask[i]){
                    r.push_back(nums[i]);
                }
            }
            res.push_back(r);
        }else{
            mask[idx] = true;
            robot(idx + 1, nums, res, mask);
            mask[idx] = false;
            robot(idx + 1, nums, res, mask);
        }
    }
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> res;
        vector<bool> mask;
        for(int i : nums){
            mask.push_back(false);
        }
        robot(0, nums, res, mask);
        return res;
    }
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 56  ms | N/A |

```python3
class Solution:
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        for i in range(2 ** len(nums)):
            mask = bin(i)[2:].rjust(len(nums), '0')
            res.append([n for j, n in enumerate(nums) if mask[j] == '1'])
        return res
```
