## 398. Random Pick Index - 随机数索引

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个可能含有重复元素的整数数组，要求随机输出给定的数字的索引。 您可以假设给定的数字一定存在于数组中。</p>

<p><strong>注意：</strong><br />
数组大小可能非常大。 使用太多额外空间的解决方案将不会通过测试。</p>

<p><strong>示例:</strong></p>

<pre>
int[] nums = new int[] {1,2,3,3,3};
Solution solution = new Solution(nums);

// pick(3) 应该返回索引 2,3 或者 4。每个索引的返回概率应该相等。
solution.pick(3);

// pick(1) 应该返回 0。因为只有nums[0]等于1。
solution.pick(1);
</pre>



-----

题目标签：Reservoir Sampling

题目链接：[LeetCode](https://leetcode.com/problems/random-pick-index/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/random-pick-index/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 76  ms | 6.4 MB |

```cpp
// refer: https://www.bilibili.com/video/av14480386/?p=2
class Solution {
public:
    vector<pair<int, int> > v;
    Solution(vector<int> nums) {
        for (int i = 0; i < nums.size(); ++i) {
            v.push_back(make_pair(nums[i], i));
        }
        sort(v.begin(), v.end());
    }
    
    int pick(int target) {
        int l = upper_bound(v.begin(), v.end(), make_pair(target, -1)) - v.begin();
        int r = upper_bound(v.begin(), v.end(), make_pair(target, INT_MAX)) - v.begin() - 1;
        return v[rand() % (r - l + 1) + l].second;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * int param_1 = obj.pick(target);
 */
```
