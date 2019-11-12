## 133. Clone Graph - 克隆图

<!--If you want to use the English description, use `question.content` instead-->

<p>给定无向<a href="https://baike.baidu.com/item/连通图/6460995?fr=aladdin" target="_blank"><strong>连通</strong></a>图中一个节点的引用，返回该图的<a href="https://baike.baidu.com/item/深拷贝/22785317?fr=aladdin" target="_blank"><strong>深拷贝</strong></a>（克隆）。图中的每个节点都包含它的值 <code>val</code>（<code>Int</code>） 和其邻居的列表（<code>list[Node]</code>）。</p>

<p><strong>示例：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/02/23/113_sample.png" style="height: 149px; width: 200px;"></p>

<pre><strong>输入：
</strong>{&quot;$id&quot;:&quot;1&quot;,&quot;neighbors&quot;:[{&quot;$id&quot;:&quot;2&quot;,&quot;neighbors&quot;:[{&quot;$ref&quot;:&quot;1&quot;},{&quot;$id&quot;:&quot;3&quot;,&quot;neighbors&quot;:[{&quot;$ref&quot;:&quot;2&quot;},{&quot;$id&quot;:&quot;4&quot;,&quot;neighbors&quot;:[{&quot;$ref&quot;:&quot;3&quot;},{&quot;$ref&quot;:&quot;1&quot;}],&quot;val&quot;:4}],&quot;val&quot;:3}],&quot;val&quot;:2},{&quot;$ref&quot;:&quot;4&quot;}],&quot;val&quot;:1}

<strong>解释：</strong>
节点 1 的值是 1，它有两个邻居：节点 2 和 4 。
节点 2 的值是 2，它有两个邻居：节点 1 和 3 。
节点 3 的值是 3，它有两个邻居：节点 2 和 4 。
节点 4 的值是 4，它有两个邻居：节点 1 和 3 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>节点数介于 1 到 100 之间。</li>
	<li>无向图是一个<a href="https://baike.baidu.com/item/简单图/1680528?fr=aladdin" target="_blank">简单图</a>，这意味着图中没有重复的边，也没有自环。</li>
	<li>由于图是无向的，如果节点 <em>p</em> 是节点 <em>q</em> 的邻居，那么节点 <em>q</em> 也必须是节点 <em>p</em>&nbsp;的邻居。</li>
	<li>必须将<strong>给定节点的拷贝</strong>作为对克隆图的引用返回。</li>
</ol>



-----

题目标签：Depth-first Search / Breadth-first Search / Graph

题目链接：[LeetCode](https://leetcode.com/problems/clone-graph/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/clone-graph/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 40  ms | 2.1 MB |

```cpp
/**
 * Definition for undirected graph.
 * struct UndirectedGraphNode {
 *     int label;
 *     vector<UndirectedGraphNode *> neighbors;
 *     UndirectedGraphNode(int x) : label(x) {};
 * };
 */
class Solution {
public:
    unordered_map<UndirectedGraphNode*, UndirectedGraphNode*> V;
    UndirectedGraphNode *cloneGraph(UndirectedGraphNode *node) {
        if (!node) return nullptr;
        if (V.count(node)) return V[node];
        // cout << node->label << ", " << node->neighbors.size() << endl;
        UndirectedGraphNode* res = new UndirectedGraphNode(node->label);
        V.insert({node, res});
        for (auto n : node->neighbors) {
            res->neighbors.push_back(cloneGraph(n));
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
