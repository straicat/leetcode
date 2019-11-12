## 384. Shuffle an Array - 打乱数组

<!--If you want to use the English description, use `question.content` instead-->

<p>打乱一个没有重复元素的数组。</p>

<p><strong>示例:</strong></p>

<pre>
// 以数字集合 1, 2 和 3 初始化数组。
int[] nums = {1,2,3};
Solution solution = new Solution(nums);

// 打乱数组 [1,2,3] 并返回结果。任何 [1,2,3]的排列返回的概率应该相同。
solution.shuffle();

// 重设数组到它的初始状态[1,2,3]。
solution.reset();

// 随机返回数组[1,2,3]打乱后的结果。
solution.shuffle();
</pre>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/shuffle-an-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shuffle-an-array/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 176  ms | 8 MB |

```cpp
// Knuth Shuffle
class Solution {
private:
    vector<int> v;
public:
    Solution(vector<int> nums) {
        v = nums;
    }
    
    /** Resets the array to its original configuration and return it. */
    vector<int> reset() {
        return v;
    }
    
    /** Returns a random shuffling of the array. */
    vector<int> shuffle() {
        vector<int> r = v;
        for (int i = r.size() - 1; i >= 0; --i) {
            int j = rand() % (i + 1);
            swap(r[i], r[j]);
        }
        return r;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * vector<int> param_1 = obj.reset();
 * vector<int> param_2 = obj.shuffle();
 */
```
