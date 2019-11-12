## 376. Wiggle Subsequence - 摆动序列

<!--If you want to use the English description, use `question.content` instead-->

<p>如果连续数字之间的差严格地在正数和负数之间交替，则数字序列称为<strong>摆动序列。</strong>第一个差（如果存在的话）可能是正数或负数。少于两个元素的序列也是摆动序列。</p>

<p>例如，&nbsp;<code>[1,7,4,9,2,5]</code> 是一个摆动序列，因为差值 <code>(6,-3,5,-7,3)</code>&nbsp;是正负交替出现的。相反, <code>[1,4,7,2,5]</code>&nbsp;和&nbsp;<code>[1,7,4,5,5]</code> 不是摆动序列，第一个序列是因为它的前两个差值都是正数，第二个序列是因为它的最后一个差值为零。</p>

<p>给定一个整数序列，返回作为摆动序列的最长子序列的长度。 通过从原始序列中删除一些（也可以不删除）元素来获得子序列，剩下的元素保持其原始顺序。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>[1,7,4,9,2,5]
<strong>输出: </strong>6 
<strong>解释: </strong>整个序列均为摆动序列。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>[1,17,5,10,13,15,10,5,16,8]
<strong>输出: </strong>7
<strong>解释: </strong>这个序列包含几个长度为 7 摆动序列，其中一个可为[1,17,10,13,10,16,8]。</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入: </strong>[1,2,3,4,5,6,7,8,9]
<strong>输出: </strong>2</pre>

<p><strong>进阶:</strong><br>
你能否用&nbsp;O(<em>n</em>) 时间复杂度完成此题?</p>



-----

题目标签：Greedy / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/wiggle-subsequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/wiggle-subsequence/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 802.8 KB |

```cpp
class Solution {
public:
    int wiggleMaxLength(vector<int>& nums) {
        if (nums.size() == 0) {
            return 0;
        }
        // p: up to current, max length
        // q: down to current, max length
        int p = 1, q = 1;
        for (int i = 1; i < (int)nums.size(); ++i) {
            if (nums[i] > nums[i-1]) {  // up
                // if up to current, then the last action should be down
                p = q + 1;
            } else if (nums[i] < nums[i-1]) {  // down
                // if down to current, then the last action should be up
                q = p + 1;
            }
        }
        return max(p, q);
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```