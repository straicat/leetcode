## 74. Search a 2D Matrix - 搜索二维矩阵

<!--If you want to use the English description, use `question.content` instead-->

<p>编写一个高效的算法来判断&nbsp;<em>m</em> x <em>n</em>&nbsp;矩阵中，是否存在一个目标值。该矩阵具有如下特性：</p>

<ul>
	<li>每行中的整数从左到右按升序排列。</li>
	<li>每行的第一个整数大于前一行的最后一个整数。</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong>
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 3
<strong>输出:</strong> true
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong>
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 13
<strong>输出:</strong> false</pre>



-----

题目标签：Array / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/search-a-2d-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-a-2d-matrix/description/)

## 题解

这题很显然用二分法。

用ruby的话，可以一行搞定~

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 0  ms | 38.6 MB |

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix.length == 0 || matrix[0].length == 0) return false;
        int l = 0, r = matrix.length - 1;
        while (l < r) {
            int m = l + r + 1 >> 1;
            if (matrix[m][0] <= target) l = m;
            else r = m - 1;
        }
        int i = l;
        l = 0; r = matrix[0].length - 1;
        while (l <= r) {
            int m = l + r >> 1;
            if (matrix[i][m] == target) return true;
            if (matrix[i][m] > target) r = m - 1;
            else l = m + 1;
        }
        return false;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| ruby  | 52  ms | N/A |

```ruby
# @param {Integer[][]} matrix
# @param {Integer} target
# @return {Boolean}
def search_matrix(matrix, target)
    return matrix.flatten.include?(target)
end
```
