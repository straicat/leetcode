## 287. Find the Duplicate Number - 寻找重复数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个包含&nbsp;<em>n</em> + 1 个整数的数组&nbsp;<em>nums</em>，其数字都在 1 到 <em>n&nbsp;</em>之间（包括 1 和 <em>n</em>），可知至少存在一个重复的整数。假设只有一个重复的整数，找出这个重复的数。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> <code>[1,3,4,2,2]</code>
<strong>输出:</strong> 2
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [3,1,3,4,2]
<strong>输出:</strong> 3
</pre>

<p><strong>说明：</strong></p>

<ol>
	<li><strong>不能</strong>更改原数组（假设数组是只读的）。</li>
	<li>只能使用额外的 <em>O</em>(1) 的空间。</li>
	<li>时间复杂度小于 <em>O</em>(<em>n</em><sup>2</sup>) 。</li>
	<li>数组中只有一个重复的数字，但它可能不止重复出现一次。</li>
</ol>



-----

题目标签：Array / Two Pointers / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/find-the-duplicate-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-the-duplicate-number/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1.9 MB |

```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int p = nums[0], q = nums[nums[0]];
        while (p != q) {
            p = nums[p];
            q = nums[nums[q]];
        }
        q = 0;
        while (p != q) {
            p = nums[p];
            q = nums[q];
        }
        return q;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
