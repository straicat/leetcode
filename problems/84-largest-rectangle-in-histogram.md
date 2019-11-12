## 84. Largest Rectangle in Histogram - 柱状图中最大的矩形

<!--If you want to use the English description, use `question.content` instead-->

<p>给定 <em>n</em> 个非负整数，用来表示柱状图中各个柱子的高度。每个柱子彼此相邻，且宽度为 1 。</p>

<p>求在该柱状图中，能够勾勒出来的矩形的最大面积。</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/histogram.png"></p>

<p><small>以上是柱状图的示例，其中每个柱子的宽度为 1，给定的高度为&nbsp;<code>[2,1,5,6,2,3]</code>。</small></p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/histogram_area.png"></p>

<p><small>图中阴影部分为所能勾勒出的最大矩形面积，其面积为&nbsp;<code>10</code>&nbsp;个单位。</small></p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [2,1,5,6,2,3]
<strong>输出:</strong> 10</pre>



-----

题目标签：Stack / Array

题目链接：[LeetCode](https://leetcode.com/problems/largest-rectangle-in-histogram/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/description/)

## 题解

![TIM图片20190405122310](https://user-images.githubusercontent.com/9983385/55603521-a61e5b00-579d-11e9-95af-292f79db5eed.jpg)

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 13  ms | 40.6 MB |

```java
class Solution {
    class Node {
        int index;
        int value;
        Node(int index, int value) {
            this.index = index;
            this.value = value;
        }
    }
    
    public int largestRectangleArea(int[] heights) {
        Stack<Node> stk = new Stack<>();
        int[] left = new int[heights.length];
        Arrays.fill(left, -1);
        for (int i = heights.length - 1; i >= 0; i--) {
            while (!stk.empty() && heights[i] < stk.peek().value) {
                left[stk.pop().index] = i;
            }
            stk.push(new Node(i, heights[i]));
        }
        //for (int i : right) System.out.print(i + " "); System.out.println();
        stk.clear();
        int[] right = new int[heights.length];
        Arrays.fill(right, heights.length);
        for (int i = 0; i < heights.length; i++) {
            while (!stk.empty() && heights[i] < stk.peek().value) {
                right[stk.pop().index] = i;
            }
            stk.push(new Node(i, heights[i]));
        }
        //for (int i : right) System.out.print(i + " "); System.out.println();
        int res = 0;
        for (int i = 0; i < heights.length; i++) {
            res = Math.max(res, heights[i] * (right[i] - left[i] - 1));
        }
        return res;
    }
}
```
