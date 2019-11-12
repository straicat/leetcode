## 971. Flip Binary Tree To Match Preorder Traversal - 翻转二叉树以匹配先序遍历

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个有 <code>N</code> 个节点的二叉树，每个节点都有一个不同于其他节点且处于 <code>{1, ..., N}</code> 中的值。</p>

<p>通过交换节点的左子节点和右子节点，可以翻转该二叉树中的节点。</p>

<p>考虑从根节点开始的先序遍历报告的 <code>N</code> 值序列。将这一 <code>N</code> 值序列称为树的行程。</p>

<p>（回想一下，节点的先序遍历意味着我们报告当前节点的值，然后先序遍历左子节点，再先序遍历右子节点。）</p>

<p>我们的目标是翻转<strong>最少的</strong>树中节点，以便树的行程与给定的行程&nbsp;<code>voyage</code>&nbsp;相匹配。&nbsp;</p>

<p>如果可以，则返回翻转的所有节点的值的列表。你可以按任何顺序返回答案。</p>

<p>如果不能，则返回列表 <code>[-1]</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/01/05/1219-01.png" style="height: 120px; width: 88px;"></strong></p>

<pre><strong>输入：</strong>root = [1,2], voyage = [2,1]
<strong>输出：</strong>[-1]
</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/01/05/1219-02.png" style="height: 120px; width: 127px;"></strong></p>

<pre><strong>输入：</strong>root = [1,2,3], voyage = [1,3,2]
<strong>输出：</strong>[1]
</pre>

<p><strong>示例 3：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/01/05/1219-02.png" style="height: 120px; width: 127px;"></strong></p>

<pre><strong>输入：</strong>root = [1,2,3], voyage = [1,2,3]
<strong>输出：</strong>[]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= N &lt;= 100</code></li>
</ol>



-----

题目标签：Tree / Depth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/flip-binary-tree-to-match-preorder-traversal/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/flip-binary-tree-to-match-preorder-traversal/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1.2 MB |

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
    vector<TreeNode*> pre;
    bool flag = true;
    vector<int> res;

    void preorder(TreeNode* node) {
        if (!node) return;
        pre.push_back(node);
        preorder(node->left);
        preorder(node->right);
    }

    void dfs(TreeNode* node, vector<int>& voy, int vst, int ved, int pst, int ped) {
        // cout << "[In] " << vst << ", " << ved << ", " << pst << ", " << ped << endl;
        if (!node) return;
        if (!flag) return;
        if (node->val != voy[vst]) {
            flag = false;
            // cout << "a" << endl;
            return;
        }
        if (ved - vst != ped - pst) {
            flag = false;
            // cout << "b" << endl;
            return;
        }
        if (ved - vst == 1 && ped - pst == 1) {
            // cout << "only root" << endl; 
            return;
        } else {
            if (ved - vst == 1) {
                flag = false;
                // cout << "c" << endl;
                return;
            }
            if (ped - pst == 1) {
                // cout << "d" << endl;
                flag = false;
                return;
            }
        }
        if (node->left && node->right) {
            if (node->left->val == voy[vst+1]) {
                int t = node->right->val;
                int x = 0, y = 0;
                for (int i=vst; i<ved; ++i) {
                    if (voy[i] == t) {
                        y = i;
                        break;
                    }
                }
                for (int i=pst; i<ped; ++i) {
                    if (pre[i]->val == t) {
                        x = i;
                        break;
                    }
                }
                if (x - pst == y - vst) {
                    dfs(node->left, voy, vst+1, y, pst+1, x);
                    dfs(node->right, voy, y, ved, x, ped);
                    return;
                }
            }
        } else {
            if (node->left) {
                if (node->left->val == voy[vst+1]) {
                    dfs(node->left, voy, vst+1, ved, pst+1, ped);
                    return;
                } else {
                    flag = false;
                    return;
                }
            }
            if (node->right) {
                if (node->right->val == voy[vst+1]) {
                    dfs(node->right, voy, vst+1, ved, pst+1, ped);
                    return;
                } else {
                    flag = false;
                    return;
                }
            }
            // cout << "leaf node!" << endl;
            return;
        }
        int x = 0;
        for (int i=pst; i<ped; ++i) {
            if (pre[i]->val == voy[vst+1]) {
                x = i;
                break;
            }
        }
        int y = 0;
        for (int i=vst; i<ved; ++i) {
            if (voy[i] == pre[pst+1]->val) {
                y = i;
                break;
            }
        }
        // cout << "x: " << x << "  y: " << y << endl;
        if (x - pst - 1 == ved - y && ped - x == y - vst - 1) {
            // cout << "push: " << voy[vst] << endl;
            res.push_back(voy[vst]);
            dfs(node->left, voy, y, ved, pst+1, x);
            dfs(node->right, voy, vst+1, y, x, ped);
        } else {
            // cout << "e" << endl;
            flag = false;
            return;
        }
    }

    vector<int> flipMatchVoyage(TreeNode* root, vector<int>& voyage) {
        if (!root || voyage.size() == 0) {
            res.push_back(-1);
            return res;
        }
        preorder(root);
        // for (auto i : pre) cout << i->val << " ";
        // cout << endl;
        dfs(root, voyage, 0, pre.size(), 0, voyage.size());
        if (!flag) {
            res.clear();
            res.push_back(-1);
            return res;
        }
        return res;
    }
};
```
