## 240. Search a 2D Matrix II - 搜索二维矩阵 II

<!--If you want to use the English description, use `question.content` instead-->

<p>编写一个高效的算法来搜索&nbsp;<em>m</em>&nbsp;x&nbsp;<em>n</em>&nbsp;矩阵 matrix 中的一个目标值 target。该矩阵具有以下特性：</p>

<ul>
	<li>每行的元素从左到右升序排列。</li>
	<li>每列的元素从上到下升序排列。</li>
</ul>

<p><strong>示例:</strong></p>

<p>现有矩阵 matrix 如下：</p>

<pre>[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
</pre>

<p>给定 target&nbsp;=&nbsp;<code>5</code>，返回&nbsp;<code>true</code>。</p>

<p>给定&nbsp;target&nbsp;=&nbsp;<code>20</code>，返回&nbsp;<code>false</code>。</p>



-----

题目标签：Binary Search / Divide and Conquer

题目链接：[LeetCode](https://leetcode.com/problems/search-a-2d-matrix-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-a-2d-matrix-ii/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 64  ms | 12.7 MB |

```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        if (matrix.size() == 0 || matrix[0].size() == 0) return false;
        int row = 0, col = matrix[0].size() - 1;
        while (col >= 0 && row < matrix.size()) {
            if (matrix[row][col] == target) return true;
            else if (matrix[row][col] > target) {
                col--;
            } else {
                row++;
            }
        }
        return false;
    }
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 5  ms | 46.1 MB |

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
        int b = l;
        for (int i = 0; i <= b; i++) {
            l = 0; r = matrix[0].length - 1;
            while (l <= r) {
                int m = l + r >> 1;
                if (matrix[i][m] == target) return true;
                if (matrix[i][m] > target) r = m - 1;
                else l = m + 1;
            }
        }
        return false;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| ruby  | 9500  ms | 182.2 MB |

```ruby
# @param {Integer[][]} matrix
# @param {Integer} target
# @return {Boolean}
def search_matrix(matrix, target)
    matrix.flatten.include?(target)
end
```
