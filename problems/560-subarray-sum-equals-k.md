## 560. Subarray Sum Equals K - 和为K的子数组

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组和一个整数&nbsp;<strong>k，</strong>你需要找到该数组中和为&nbsp;<strong>k&nbsp;</strong>的连续的子数组的个数。</p>

<p><strong>示例 1 :</strong></p>

<pre>
<strong>输入:</strong>nums = [1,1,1], k = 2
<strong>输出:</strong> 2 , [1,1] 与 [1,1] 为两种不同的情况。
</pre>

<p><strong>说明 :</strong></p>

<ol>
	<li>数组的长度为 [1, 20,000]。</li>
	<li>数组中元素的范围是 [-1000, 1000] ，且整数&nbsp;<strong>k&nbsp;</strong>的范围是&nbsp;[-1e7, 1e7]。</li>
</ol>



-----

题目标签：Array / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/subarray-sum-equals-k/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/subarray-sum-equals-k/description/)

## 题解

注意：`unordered_map`的`.count`返回拥有比较等于指定参数 key 的关键的元素数，因为此容器不允许重复故为 1 或 0 。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 28  ms | 3.3 MB |

```cpp
static int x=[](){
    ios::sync_with_stdio(false);
    cin.tie(0); cout.tie(0);
    return 0;
}();

class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        int res = 0;
        int a = 0;
        unordered_map<int, int> mm;
        mm[0] = 1;
        for (int num : nums) {
            a += num;
            res += mm[a - k];
            mm[a]++;
        }
        return res;
    }
};
```
