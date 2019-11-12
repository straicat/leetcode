## 123. Best Time to Buy and Sell Stock III - 买卖股票的最佳时机 III

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个数组，它的第<em> i</em> 个元素是一支给定的股票在第 <em>i </em>天的价格。</p>

<p>设计一个算法来计算你所能获取的最大利润。你最多可以完成&nbsp;<em>两笔&nbsp;</em>交易。</p>

<p><strong>注意:</strong>&nbsp;你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> [3,3,5,0,0,3,1,4]
<strong>输出:</strong> 6
<strong>解释:</strong> 在第 4 天（股票价格 = 0）的时候买入，在第 6 天（股票价格 = 3）的时候卖出，这笔交易所能获得利润 = 3-0 = 3 。
&nbsp;    随后，在第 7 天（股票价格 = 1）的时候买入，在第 8 天 （股票价格 = 4）的时候卖出，这笔交易所能获得利润 = 4-1 = 3 。</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> [1,2,3,4,5]
<strong>输出:</strong> 4
<strong>解释:</strong> 在第 1 天（股票价格 = 1）的时候买入，在第 5 天 （股票价格 = 5）的时候卖出, 这笔交易所能获得利润 = 5-1 = 4 。 &nbsp; 
&nbsp;    注意你不能在第 1 天和第 2 天接连购买股票，之后再将它们卖出。 &nbsp; 
&nbsp;    因为这样属于同时参与了多笔交易，你必须在再次购买前出售掉之前的股票。
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入:</strong> [7,6,4,3,1] 
<strong>输出:</strong> 0 
<strong>解释:</strong> 在这个情况下, 没有交易完成, 所以最大利润为 0。</pre>



-----

题目标签：Array / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-iii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 1  ms | 37.7 MB |

```java
class Solution {
    public int maxProfit(int[] prices) {
        // 第1次买入，第1次卖出，第2次买入，第2次卖出
        int[] v = new int[]{Integer.MIN_VALUE, 0, Integer.MIN_VALUE, 0};
        for (int p : prices) {
            v[0] = Math.max(v[0], -p);
            v[1] = Math.max(v[1], v[0] + p);
            v[2] = Math.max(v[2], v[1] - p);
            v[3] = Math.max(v[3], v[2] + p);
        }
        return v[3];
    }
}
```
