## 867. Transpose Matrix - 转置矩阵

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个矩阵&nbsp;<code>A</code>，&nbsp;返回&nbsp;<code>A</code>&nbsp;的转置矩阵。</p>

<p>矩阵的转置是指将矩阵的主对角线翻转，交换矩阵的行索引与列索引。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[[1,2,3],[4,5,6],[7,8,9]]
<strong>输出：</strong>[[1,4,7],[2,5,8],[3,6,9]]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[[1,2,3],[4,5,6]]
<strong>输出：</strong>[[1,4],[2,5],[3,6]]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length&nbsp;&lt;= 1000</code></li>
	<li><code>1 &lt;= A[0].length&nbsp;&lt;= 1000</code></li>
</ol>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/transpose-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/transpose-matrix/description/)

## 题解

Python里转置矩阵写法非常简单：`list(zip(*A))`

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 92  ms | N/A |

```python3
class Solution:
    def transpose(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        return list(zip(*A))
```
