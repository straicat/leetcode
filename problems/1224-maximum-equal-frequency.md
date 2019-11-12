## 1224. Maximum Equal Frequency - 最大相等频率

<!--If you want to use the English description, use `question.content` instead-->

<p>给出一个正整数数组&nbsp;<code>nums</code>，请你帮忙从该数组中找出能满足下面要求的 <strong>最长</strong> 前缀，并返回其长度：</p>

<ul>
	<li>从前缀中 <strong>删除一个</strong> 元素后，使得所剩下的每个数字的出现次数相同。</li>
</ul>

<p>如果删除这个元素后没有剩余元素存在，仍可认为每个数字都具有相同的出现次数（也就是 0 次）。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [2,2,1,1,5,3,3,5]
<strong>输出：</strong>7
<strong>解释：</strong>对于长度为 7 的子数组 [2,2,1,1,5,3,3]，如果我们从中删去 nums[4]=5，就可以得到 [2,2,1,1,3,3]，里面每个数字都出现了两次。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [1,1,1,2,2,2,3,3,3,4,4,4,5]
<strong>输出：</strong>13
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>nums = [1,1,1,2,2,2]
<strong>输出：</strong>5
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>nums = [10,2,8,9,3,8,1,5,2,3,7,6]
<strong>输出：</strong>8
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10^5</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10^5</code></li>
</ul>



-----

题目标签：Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/maximum-equal-frequency/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-equal-frequency/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 88  ms | 18.4 MB |

```cpp
class Solution {
public:
    int maxEqualFreq(vector<int>& nums) {
        unordered_map<int, int> cnt;
        unordered_map<int, int> times;
        for (int num : nums) {
            cnt[num]++;
        }
        for (auto t = cnt.begin(); t != cnt.end(); t++) {
            times[t->second]++;
        }
        int res = nums.size();
        while (res > 0) {
            // cout << res << "\t| "; for (auto t = times.begin(); t != times.end(); t++) cout << t->first << ": " << t->second << "\t"; cout << endl;
            
            // 只有一种出现次数时，存在两种可能的情况：
            // 1. 出现1次的有x个，此时所有数都不一样
            // 2. 出现x次的只有1个，此时所有数都一样
            if (times.size() == 1 && (times.begin()->first == 1 || times.begin()->second == 1)) {
                return res;
            }
            if (times.size() == 2) {
                auto t = times.begin();
                auto a = t;
                t++;
                auto b = t;
                // 只有两种出现次数时，存在两种可能的情况：
                // 1. 出现1次的只有1个
                // 2. 出现n次的只有1个，且另一个是出现n-1次
                if (a->second == 1 && (a->first == 1 || a->first - 1 == b->first)) {
                    return res;
                }
                if (b->second == 1 && (b->first == 1 || b->first - 1 == a->first)) {
                    return res;
                }
            }
            
            res--;
            times[cnt[nums[res]]]--;
            // 当某个出现次数减为0时，从times中移除
            if (times[cnt[nums[res]]] == 0) {
                times.erase(cnt[nums[res]]);
            }
            cnt[nums[res]]--;
            // 注意：当出现次数为0时，不计入times
            if (cnt[nums[res]] > 0) {
                times[cnt[nums[res]]]++;
            }
        }
        return res;
    }
};
```
