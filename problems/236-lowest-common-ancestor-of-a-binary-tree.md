## 236. Lowest Common Ancestor of a Binary Tree - 二叉树的最近公共祖先

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。</p>

<p><a href="https://baike.baidu.com/item/%E6%9C%80%E8%BF%91%E5%85%AC%E5%85%B1%E7%A5%96%E5%85%88/8918834?fr=aladdin" target="_blank">百度百科</a>中最近公共祖先的定义为：&ldquo;对于有根树 T 的两个结点 p、q，最近公共祖先表示为一个结点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大（<strong>一个节点也可以是它自己的祖先</strong>）。&rdquo;</p>

<p>例如，给定如下二叉树:&nbsp; root =&nbsp;[3,5,1,6,2,0,8,null,null,7,4]</p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/15/binarytree.png" style="height: 190px; width: 200px;"></p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
<strong>输出:</strong> 3
<strong>解释: </strong>节点 <code>5 </code>和节点 <code>1 </code>的最近公共祖先是节点 <code>3。</code>
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
<strong>输出:</strong> 5
<strong>解释: </strong>节点 <code>5 </code>和节点 <code>4 </code>的最近公共祖先是节点 <code>5。</code>因为根据定义最近公共祖先节点可以为节点本身。
</pre>

<p>&nbsp;</p>

<p><strong>说明:</strong></p>

<ul>
	<li>所有节点的值都是唯一的。</li>
	<li>p、q 为不同节点且均存在于给定的二叉树中。</li>
</ul>



-----

题目标签：Tree

题目链接：[LeetCode](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 8  ms | 3 MB |

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    void dfs(TreeNode* node, TreeNode* target, vector<TreeNode*>& path, bool& ret) {
        if (!node || ret) return;

        if (!ret && node == target) {
            ret = true;
        }

        path.push_back(node);

        if (!ret && node->left) {
            dfs(node->left, target, path, ret);
        }
        if (!ret && node->right) {
            dfs(node->right, target, path, ret);
        }

        if (!ret) {
            path.pop_back();
        }
    }

    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if (root == NULL) return NULL;

        vector<TreeNode*> pp;
        bool r1 = false;
        dfs(root, p, pp, r1);

        vector<TreeNode*> pq;
        bool r2 = false;
        dfs(root, q, pq, r2);

        int i = 0;
        for (; i < pp.size() && i < pq.size() && pp[i] == pq[i]; ++i) ;
        i--;  // main reason for runtime error
        // runtime error: member access within misaligned address 0x000000000021 for type 'struct TreeNode', which requires 8 byte alignment
        return pp[i];
        
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
