## 338. Counting Bits - 比特位计数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非负整数&nbsp;<strong>num</strong>。对于&nbsp;<strong>0 &le; i &le; num </strong>范围中的每个数字&nbsp;<strong>i&nbsp;</strong>，计算其二进制数中的 1 的数目并将它们作为数组返回。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong>2
<strong>输出: </strong>[0,1,1]</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入: </strong>5
<strong>输出: </strong><code>[0,1,1,2,1,2]</code></pre>

<p><strong>进阶:</strong></p>

<ul>
	<li>给出时间复杂度为<strong>O(n*sizeof(integer))</strong>的解答非常容易。但你可以在线性时间<strong>O(n)</strong>内用一趟扫描做到吗？</li>
	<li>要求算法的空间复杂度为<strong>O(n)</strong>。</li>
	<li>你能进一步完善解法吗？要求在C++或任何其他语言中不使用任何内置函数（如 C++ 中的&nbsp;<strong>__builtin_popcount</strong>）来执行此操作。</li>
</ul>



-----

题目标签：Bit Manipulation / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/counting-bits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/counting-bits/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 116  ms | N/A |

```python3
class Solution:
    def countBits(self, num):
        """
        :type num: int
        :rtype: List[int]
        """
        tmp = [0]
        for i in range(1, num+1):
            tmp.append(tmp[i>>1] + i%2)
        return tmp
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 3  ms | N/A |

```java
class Solution {
    public int[] countBits(int num) {
        int[] f = new int[num + 1];
        for (int i=1; i<=num; i++) f[i] = f[i >> 1] + (i & 1);
    return f;
}
}
```
