## 532. K-diff Pairs in an Array - 数组中的K-diff数对

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数数组和一个整数&nbsp;<strong>k</strong>, 你需要在数组里找到<strong>不同的&nbsp;</strong>k-diff 数对。这里将&nbsp;<strong>k-diff</strong>&nbsp;数对定义为一个整数对 (i, j), 其中<strong> i </strong>和<strong> j </strong>都是数组中的数字，且两数之差的绝对值是&nbsp;<strong>k</strong>.</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [3, 1, 4, 1, 5], k = 2
<strong>输出:</strong> 2
<strong>解释: </strong>数组中有两个 2-diff 数对, (1, 3) 和 (3, 5)。
尽管数组中有两个1，但我们只应返回不同的数对的数量。
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre>
<strong>输入:</strong>[1, 2, 3, 4, 5], k = 1
<strong>输出: </strong>4
<strong>解释:</strong> 数组中有四个 1-diff 数对, (1, 2), (2, 3), (3, 4) 和 (4, 5)。
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入: </strong>[1, 3, 1, 5, 4], k = 0
<strong>输出: </strong>1
<strong>解释:</strong> 数组中只有一个 0-diff 数对，(1, 1)。
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>数对 (i, j) 和数对&nbsp;(j, i) 被算作同一数对。</li>
	<li>数组的长度不超过10,000。</li>
	<li>所有输入的整数的范围在&nbsp;[-1e7, 1e7]。</li>
</ol>



-----

题目标签：Array / Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/k-diff-pairs-in-an-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/k-diff-pairs-in-an-array/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| c  | 1006  ms | N/A |

```c
#include<stdio.h>
#include<math.h>
#define MAX 10000

int findPairs(int* nums, int numsSize, int k) {
    int cnt = 0;
    int kPairs[MAX][2];
    for (int i = 0; i < numsSize - 1; i++)
    {
        for (int j = i + 1; j < numsSize; j++)
        {
            int flag = 1;
            int a = *(nums + i), b = *(nums + j);
            if (abs(a - b) == k)
            {
                for (int k = 0; k < cnt; k++)
                {
                    if ((a == kPairs[k][0] && b == kPairs[k][1]) || (a == kPairs[k][1] && b == kPairs[k][0]))
                        flag = 0;
                }
                if (flag)
                {
                    kPairs[cnt][0] = a;
                    kPairs[cnt][1] = b;
                    cnt++;
                }
            }
        }
    }
    return cnt;
}
```
