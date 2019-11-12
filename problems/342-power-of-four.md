## 342. Power of Four - 4的幂

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数 (32 位有符号整数)，请编写一个函数来判断它是否是 4&nbsp;的幂次方。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>16
<strong>输出: </strong>true
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>5
<strong>输出: </strong>false</pre>

<p><strong>进阶：</strong><br>
你能不使用循环或者递归来完成本题吗？</p>



-----

题目标签：Bit Manipulation

题目链接：[LeetCode](https://leetcode.com/problems/power-of-four/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/power-of-four/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 839.7 KB |

```cpp
class Solution {
public:
    bool isPowerOfFour(int num) {
        return num > 0 && !(num & (num - 1)) && !((num - 1) % 3); 
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
