## 999. Available Captures for Rook - 车的可用捕获量

<!--If you want to use the English description, use `question.content` instead-->

<p>在一个 8 x 8 的棋盘上，有一个白色车（rook）。也可能有空方块，白色的象（bishop）和黑色的卒（pawn）。它们分别以字符 &ldquo;R&rdquo;，&ldquo;.&rdquo;，&ldquo;B&rdquo; 和 &ldquo;p&rdquo; 给出。大写字符表示白棋，小写字符表示黑棋。</p>

<p>车按国际象棋中的规则移动：它选择四个基本方向中的一个（北，东，西和南），然后朝那个方向移动，直到它选择停止、到达棋盘的边缘或移动到同一方格来捕获该方格上颜色相反的卒。另外，车不能与其他友方（白色）象进入同一个方格。</p>

<p>返回车能够在一次移动中捕获到的卒的数量。<br>
&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/23/1253_example_1_improved.PNG" style="height: 305px; width: 300px;"></p>

<pre><strong>输入：</strong>[[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;p&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;R&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;p&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;p&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;]]
<strong>输出：</strong>3
<strong>解释：
</strong>在本例中，车能够捕获所有的卒。
</pre>

<p><strong>示例 2：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/23/1253_example_2_improved.PNG" style="height: 306px; width: 300px;"></p>

<pre><strong>输入：</strong>[[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;p&quot;,&quot;p&quot;,&quot;p&quot;,&quot;p&quot;,&quot;p&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;p&quot;,&quot;p&quot;,&quot;B&quot;,&quot;p&quot;,&quot;p&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;p&quot;,&quot;B&quot;,&quot;R&quot;,&quot;B&quot;,&quot;p&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;p&quot;,&quot;p&quot;,&quot;B&quot;,&quot;p&quot;,&quot;p&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;p&quot;,&quot;p&quot;,&quot;p&quot;,&quot;p&quot;,&quot;p&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;]]
<strong>输出：</strong>0
<strong>解释：
</strong>象阻止了车捕获任何卒。
</pre>

<p><strong>示例 3：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/23/1253_example_3_improved.PNG" style="height: 305px; width: 300px;"></p>

<pre><strong>输入：</strong>[[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;p&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;p&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;p&quot;,&quot;p&quot;,&quot;.&quot;,&quot;R&quot;,&quot;.&quot;,&quot;p&quot;,&quot;B&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;B&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;p&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;.&quot;]]
<strong>输出：</strong>3
<strong>解释： </strong>
车可以捕获位置 b5，d6 和 f5 的卒。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>board.length == board[i].length == 8</code></li>
	<li><code>board[i][j]</code> 可以是&nbsp;<code>&#39;R&#39;</code>，<code>&#39;.&#39;</code>，<code>&#39;B&#39;</code>&nbsp;或&nbsp;<code>&#39;p&#39;</code></li>
	<li>只有一个格子上存在&nbsp;<code>board[i][j] == &#39;R&#39;</code></li>
</ol>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/available-captures-for-rook/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/available-captures-for-rook/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 0  ms | 35.4 MB |

```java
class Solution {
    public int numRookCaptures(char[][] board) {
        int n = 8;
        int res = 0;
        // 找到white rook的位置
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (board[i][j] == 'R') {
                    // 从white rook的位置往4个方向进行扩展
                    for (int x = i, y = j; x >= 0; x--) {
                        if (board[x][y] == 'p') {
                            res += 1;
                            break;
                        } else if (board[x][y] == 'B') {
                            break;
                        }
                    }
                    for (int x = i, y = j; x < n; x++) {
                        if (board[x][y] == 'p') {
                            res += 1;
                            break;
                        } else if (board[x][y] == 'B') {
                            break;
                        }
                    }
                    for (int x = i, y = j; y >= 0; y--) {
                        if (board[x][y] == 'p') {
                            res += 1;
                            break;
                        } else if (board[x][y] == 'B') {
                            break;
                        }
                    }
                    for (int x = i, y = j; y < n; y++) {
                        if (board[x][y] == 'p') {
                            res += 1;
                            break;
                        } else if (board[x][y] == 'B') {
                            break;
                        }
                    }
                    break;
                }
            }
        }
        return res;
    }
}
```
