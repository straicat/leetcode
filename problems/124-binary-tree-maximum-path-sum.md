## 124. Binary Tree Maximum Path Sum - 二叉树中的最大路径和

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个<strong>非空</strong>二叉树，返回其最大路径和。</p>

<p>本题中，路径被定义为一条从树中任意节点出发，达到任意节点的序列。该路径<strong>至少包含一个</strong>节点，且不一定经过根节点。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> [1,2,3]

       <strong>1</strong>
      <strong>/ \</strong>
     <strong>2</strong>   <strong>3</strong>

<strong>输出:</strong> 6
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> [-10,9,20,null,null,15,7]

&nbsp;  -10
&nbsp; &nbsp;/ \
&nbsp; 9 &nbsp;<strong>20</strong>
&nbsp; &nbsp; <strong>/ &nbsp;\</strong>
&nbsp; &nbsp;<strong>15 &nbsp; 7</strong>

<strong>输出:</strong> 42</pre>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/binary-tree-maximum-path-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-tree-maximum-path-sum/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 1  ms | 40.7 MB |

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    private int ret = Integer.MIN_VALUE;

    private int findBest(TreeNode root) {
        if (root == null)
            return 0;
        
        int left = Math.max(0, findBest(root.left));
        int right = Math.max(0, findBest(root.right));

        int sum = root.val + left + right;
        ret = Math.max(ret, sum);

        return root.val + Math.max(left, right);
    }

    public int maxPathSum(TreeNode root) {
        findBest(root);
        return ret;
    }
}
```
