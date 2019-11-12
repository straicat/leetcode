## 239. Sliding Window Maximum - 滑动窗口最大值

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个数组 <em>nums</em>，有一个大小为&nbsp;<em>k&nbsp;</em>的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到在滑动窗口内的 <em>k</em>&nbsp;个数字。滑动窗口每次只向右移动一位。</p>

<p>返回滑动窗口中的最大值。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> <em>nums</em> = <code>[1,3,-1,-3,5,3,6,7]</code>, 和 <em>k</em> = 3
<strong>输出: </strong><code>[3,3,5,5,6,7] 
<strong>解释: 
</strong></code>
  滑动窗口的位置                最大值
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<p>你可以假设 <em>k </em>总是有效的，在输入数组不为空的情况下，1 &le; k &le;&nbsp;输入数组的大小。</p>

<p>&nbsp;</p>

<p><strong>进阶：</strong></p>

<p>你能在线性时间复杂度内解决此题吗？</p>



-----

题目标签：Heap / Sliding Window

题目链接：[LeetCode](https://leetcode.com/problems/sliding-window-maximum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sliding-window-maximum/description/)

## 题解

![OJ草稿-16-1](https://user-images.githubusercontent.com/9983385/55632833-a9413780-57ed-11e9-97e3-25aa87633b08.jpg)



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 7  ms | 42.9 MB |

```java
class Solution {
    class Node {
        int index;
        int value;
        Node(int index, int value) {
            this.index = index;
            this.value = value;
        }
    }

    public int[] maxSlidingWindow(int[] nums, int k) {
        if (k == 0 || nums.length == 0) return new int[0];
        LinkedList<Node> list = new LinkedList<>();
        int[] ans = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            while (!list.isEmpty() && list.getLast().value <= nums[i]) {
                list.removeLast();
            }
            while (!list.isEmpty() && i - list.getFirst().index >= k) {
                list.removeFirst();
            }
            list.addLast(new Node(i, nums[i]));
            ans[i] = list.getFirst().value;
        }
        return Arrays.copyOfRange(ans, k - 1, ans.length);
    }
}
```
