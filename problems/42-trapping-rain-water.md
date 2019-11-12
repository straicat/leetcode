## 42. Trapping Rain Water - 接雨水

<!--If you want to use the English description, use `question.content` instead-->

<p>给定&nbsp;<em>n</em> 个非负整数表示每个宽度为 1 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/rainwatertrap.png" style="height: 161px; width: 412px;"></p>

<p><small>上面是由数组 [0,1,0,2,1,0,1,3,2,1,2,1] 表示的高度图，在这种情况下，可以接 6 个单位的雨水（蓝色部分表示雨水）。&nbsp;<strong>感谢 Marcos</strong> 贡献此图。</small></p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [0,1,0,2,1,0,1,3,2,1,2,1]
<strong>输出:</strong> 6</pre>



-----

题目标签：Stack / Array / Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/trapping-rain-water/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/trapping-rain-water/description/)

## 题解

![OJ草稿-13](https://user-images.githubusercontent.com/9983385/55602552-cef02180-5798-11e9-8d30-b0fd35be9096.jpg)

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 1  ms | 38.6 MB |

```java
class Solution {
    public int trap(int[] height) {
        int n = height.length;
        if (n < 3) return 0;
        int[] left = new int[n];
        left[0] = height[0];
        for (int i = 1; i < n; i++) {
            left[i] = Math.max(left[i - 1], height[i]);
        }
        int[] right = new int[n];
        right[n - 1] = height[n - 1];
        for (int i = n - 2; i >= 0; i--) {
            right[i] = Math.max(right[i + 1], height[i]);
        }
        int res = 0;
        for (int i = 0; i < n; i++) {
            res += Math.min(left[i], right[i]) - height[i];
        }
        return res;
    }
}
```
