## 832. Flipping an Image - 翻转图像

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二进制矩阵&nbsp;<code>A</code>，我们想先水平翻转图像，然后反转图像并返回结果。</p>

<p>水平翻转图片就是将图片的每一行都进行翻转，即逆序。例如，水平翻转&nbsp;<code>[1, 1, 0]</code>&nbsp;的结果是&nbsp;<code>[0, 1, 1]</code>。</p>

<p>反转图片的意思是图片中的&nbsp;<code>0</code>&nbsp;全部被&nbsp;<code>1</code>&nbsp;替换，&nbsp;<code>1</code>&nbsp;全部被&nbsp;<code>0</code>&nbsp;替换。例如，反转&nbsp;<code>[0, 1, 1]</code>&nbsp;的结果是&nbsp;<code>[1, 0, 0]</code>。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入: </strong>[[1,1,0],[1,0,1],[0,0,0]]
<strong>输出: </strong>[[1,0,0],[0,1,0],[1,1,1]]
<strong>解释:</strong> 首先翻转每一行: [[0,1,1],[1,0,1],[0,0,0]]；
     然后反转图片: [[1,0,0],[0,1,0],[1,1,1]]
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入: </strong>[[1,1,0,0],[1,0,0,1],[0,1,1,1],[1,0,1,0]]
<strong>输出: </strong>[[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
<strong>解释:</strong> 首先翻转每一行: [[0,0,1,1],[1,0,0,1],[1,1,1,0],[0,1,0,1]]；
     然后反转图片: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
</pre>

<p><strong>说明:</strong></p>

<ul>
	<li><code>1 &lt;= A.length = A[0].length &lt;= 20</code></li>
	<li><code>0 &lt;= A[i][j]&nbsp;&lt;=&nbsp;1</code></li>
</ul>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/flipping-an-image/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/flipping-an-image/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 64  ms | N/A |

```python3
class Solution:
    def flipAndInvertImage(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        rst = []
        for a in A:
            a.reverse()
            rst.append(list(map(lambda x: x ^ 1, a)))
        return rst
```
