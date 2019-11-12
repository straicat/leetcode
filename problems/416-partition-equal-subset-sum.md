## 416. Partition Equal Subset Sum - 分割等和子集

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个<strong>只包含正整数</strong>的<strong>非空</strong>数组。是否可以将这个数组分割成两个子集，使得两个子集的元素和相等。</p>

<p><strong>注意:</strong></p>

<ol>
	<li>每个数组中的元素不会超过 100</li>
	<li>数组的大小不会超过 200</li>
</ol>

<p><strong>示例 1:</strong></p>

<pre>输入: [1, 5, 11, 5]

输出: true

解释: 数组可以分割成 [1, 5, 5] 和 [11].
</pre>

<p>&nbsp;</p>

<p><strong>示例&nbsp;2:</strong></p>

<pre>输入: [1, 2, 3, 5]

输出: false

解释: 数组不能分割成两个元素和相等的子集.
</pre>

<p>&nbsp;</p>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/partition-equal-subset-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/partition-equal-subset-sum/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 880.6 KB |

```cpp
const int N = 20000;

static const auto io_sync_off = [](){
    // turn off sync
    std::ios::sync_with_stdio(false);
    // untie in/out streams
    std::cin.tie(nullptr);
    return nullptr;
}();

class Solution {
public:
    bool canPartition(vector<int>& nums) {
        int sum = accumulate(nums.begin(), nums.end(), 0);
        if (sum % 2) {
            return false;
        }
        bitset<N> bs;
        bitset<N> one(1);
        for (int num : nums) {
            bs |= (bs << num);
            bs |= (one << num);
            if (bs[sum / 2]) {
                return true;
            }
        }
        return bs[sum / 2];
    }
};
```
