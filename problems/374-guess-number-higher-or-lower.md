## 374. Guess Number Higher or Lower - 猜数字大小

<!--If you want to use the English description, use `question.content` instead-->

<p>我们正在玩一个猜数字游戏。 游戏规则如下：<br>
我从&nbsp;<strong>1</strong>&nbsp;到&nbsp;<em><strong>n</strong></em>&nbsp;选择一个数字。 你需要猜我选择了哪个数字。<br>
每次你猜错了，我会告诉你这个数字是大了还是小了。<br>
你调用一个预先定义好的接口&nbsp;<code>guess(int num)</code>，它会返回 3 个可能的结果（<code>-1</code>，<code>1</code>&nbsp;或 <code>0</code>）：</p>

<pre>-1 : 我的数字比较小
 1 : 我的数字比较大
 0 : 恭喜！你猜对了！
</pre>

<p><strong>示例 :</strong></p>

<pre><strong>输入: </strong>n = 10, pick = 6
<strong>输出: </strong>6</pre>



-----

题目标签：Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/guess-number-higher-or-lower/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/guess-number-higher-or-lower/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 823.3 KB |

```cpp
// Forward declaration of guess API.
// @param num, your guess
// @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
int guess(int num);

class Solution {
public:
    int guessNumber(int n) {
        int low = 1, high = n;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            int ans = guess(mid);
            if (ans == 0) {
                return mid;
            } else if (ans == -1) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return -1;
    }
};
```
