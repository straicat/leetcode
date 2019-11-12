## 414. Third Maximum Number - 第三大的数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非空数组，返回此数组中第三大的数。如果不存在，则返回数组中最大的数。要求算法时间复杂度必须是O(n)。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> [3, 2, 1]

<strong>输出:</strong> 1

<strong>解释:</strong> 第三大的数是 1.
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> [1, 2]

<strong>输出:</strong> 2

<strong>解释:</strong> 第三大的数不存在, 所以返回最大的数 2 .
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> [2, 2, 3, 1]

<strong>输出:</strong> 1

<strong>解释:</strong> 注意，要求返回第三大的数，是指第三大且唯一出现的数。
存在两个值为2的数，它们都排第二。
</pre>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/third-maximum-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/third-maximum-number/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| c  | 6  ms | N/A |

```c
int thirdMax(int* nums, int numsSize) {
    int *a[3] = { NULL, NULL, NULL };
    for (int i = 0; i < numsSize; i++, nums++) {
        if (a[0] == NULL) {
            a[0] = nums;
        }
        else {
            if (*nums > *a[0]) {
                if (a[1] == NULL) {
                    a[1] = a[0];
                }
                else {
                    if (*a[1] > *a[0]) {
                        if (a[2] == NULL || *a[0] > *a[2]) {
                            a[2] = a[0];
                        }
                    }
                    if (*a[1] < *a[0]) {
                        if (a[2] == NULL || *a[1] > *a[2]) {
                            a[2] = a[1];
                        }
                        a[1] = a[0];
                    }
                }
                a[0] = nums;
            }
            if (*nums < *a[0]) {
                if (a[1] == NULL) {
                    a[1] = nums;
                }
                else {
                    if (*a[1] > *nums) {
                        if (a[2] == NULL || *a[2] < *nums) {
                            a[2] = nums;
                        }
                    }
                    if (*a[1] < *nums) {
                        if (a[2] == NULL || *a[2] < *a[1]) {
                            a[2] = a[1];
                        }
                        a[1] = nums;
                    }
                }
            }
        }
    }
    if (a[2] == NULL)
        return *a[0];
    else
        return *a[2];
}
```
