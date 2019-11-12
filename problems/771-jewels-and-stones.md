## 771. Jewels and Stones - 宝石与石头

<!--If you want to use the English description, use `question.content` instead-->

<p>&nbsp;给定字符串<code>J</code>&nbsp;代表石头中宝石的类型，和字符串&nbsp;<code>S</code>代表你拥有的石头。&nbsp;<code>S</code>&nbsp;中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。</p>

<p><code>J</code>&nbsp;中的字母不重复，<code>J</code>&nbsp;和&nbsp;<code>S</code>中的所有字符都是字母。字母区分大小写，因此<code>&quot;a&quot;</code>和<code>&quot;A&quot;</code>是不同类型的石头。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> J = &quot;aA&quot;, S = &quot;aAAbbbb&quot;
<strong>输出:</strong> 3
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> J = &quot;z&quot;, S = &quot;ZZ&quot;
<strong>输出:</strong> 0
</pre>

<p><strong>注意:</strong></p>

<ul>
	<li><code>S</code>&nbsp;和&nbsp;<code>J</code>&nbsp;最多含有50个字母。</li>
	<li>&nbsp;<code>J</code>&nbsp;中的字符不重复。</li>
</ul>



-----

题目标签：Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/jewels-and-stones/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/jewels-and-stones/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 40  ms | N/A |

```python3
class Solution:
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        return sum(map(lambda x: S.count(x), J))
```
