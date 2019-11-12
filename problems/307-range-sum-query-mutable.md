## 307. Range Sum Query - Mutable - 区域和检索 - 数组可修改

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组 &nbsp;<em>nums</em>，求出数组从索引&nbsp;<em>i&nbsp;</em>到&nbsp;<em>j&nbsp;&nbsp;</em>(<em>i</em>&nbsp;&le;&nbsp;<em>j</em>) 范围内元素的总和，包含&nbsp;<em>i,&nbsp; j&nbsp;</em>两点。</p>

<p><em>update(i, val)</em> 函数可以通过将下标为&nbsp;<em>i&nbsp;</em>的数值更新为&nbsp;<em>val</em>，从而对数列进行修改。</p>

<p><strong>示例:</strong></p>

<pre>Given nums = [1, 3, 5]

sumRange(0, 2) -&gt; 9
update(1, 2)
sumRange(0, 2) -&gt; 8
</pre>

<p><strong>说明:</strong></p>

<ol>
	<li>数组仅可以在&nbsp;<em>update&nbsp;</em>函数下进行修改。</li>
	<li>你可以假设 <em>update</em> 函数与 <em>sumRange</em> 函数的调用次数是均匀分布的。</li>
</ol>



-----

题目标签：Binary Indexed Tree / Segment Tree

题目链接：[LeetCode](https://leetcode.com/problems/range-sum-query-mutable/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/range-sum-query-mutable/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 20  ms | 6.2 MB |

```cpp
// refer: https://www.bilibili.com/video/av15683671
class NumArray {
public:
    vector<int> tree;
    int size;
    NumArray(vector<int> nums) {
        if (nums.empty()) {
            return;
        }
        size = nums.size();
        tree = vector<int>(size * 2, 0);
        // fill in nums values
        for (int i = size; i < size * 2; ++i) {
            tree[i] = nums[i - size];
        }
        // fill in range sums
        for (int i = size - 1; i > 0; --i) {
            tree[i] = tree[2 * i] + tree[2 * i + 1];
        }
    }
    
    void update(int i, int val) {
        i += size;
        tree[i] = val;
        while (i > 0) {
            int left = i;
            int right = i;
            // i is left node
            if (i % 2 == 0) {
                right = i + 1;
            } else {  // i is right node
                left = i - 1;
            }
            i /= 2;
            tree[i] = tree[left] + tree[right];  // update parent node
        }
    }
    
    int sumRange(int i, int j) {
        i += size;
        j += size;
        int sum = 0;
        while (i <= j) {
            if (i % 2 == 1) {
                sum += tree[i];
                i++;
            }
            if (j % 2 == 0) {
                sum += tree[j];
                j--;
            }
            i /= 2;
            j /= 2;
        }
        return sum;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray obj = new NumArray(nums);
 * obj.update(i,val);
 * int param_2 = obj.sumRange(i,j);
 */
```
