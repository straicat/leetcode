## 476. Number Complement - 数字的补数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个正整数，输出它的补数。补数是对该数的二进制表示取反。</p>

<p><strong>注意:</strong></p>

<ol>
	<li>给定的整数保证在32位带符号整数的范围内。</li>
	<li>你可以假定二进制数不包含前导零位。</li>
</ol>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> 5
<strong>输出:</strong> 2
<strong>解释:</strong> 5的二进制表示为101（没有前导零位），其补数为010。所以你需要输出2。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> 1
<strong>输出:</strong> 0
<strong>解释:</strong> 1的二进制表示为1（没有前导零位），其补数为0。所以你需要输出0。
</pre>



-----

题目标签：Bit Manipulation

题目链接：[LeetCode](https://leetcode.com/problems/number-complement/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-complement/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 8.2 MB |

```cpp
class Solution {
public:
    int findComplement(int num) {
        bool flag = false;
        for (int i = 31; i >= 0; i--) {
            if (num & (1 << i)) {
                flag = true;
                num ^= (1 << i);
            } else {
                if (flag) {
                    num ^= (1 << i);
                }
            }
        }
        return num;
    }
};
```
