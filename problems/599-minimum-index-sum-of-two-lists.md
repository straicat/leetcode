## 599. Minimum Index Sum of Two Lists - 两个列表的最小索引总和

<!--If you want to use the English description, use `question.content` instead-->

<p>假设Andy和Doris想在晚餐时选择一家餐厅，并且他们都有一个表示最喜爱餐厅的列表，每个餐厅的名字用字符串表示。</p>

<p>你需要帮助他们用<strong>最少的索引和</strong>找出他们<strong>共同喜爱的餐厅</strong>。 如果答案不止一个，则输出所有答案并且不考虑顺序。 你可以假设总是存在一个答案。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong>
[&quot;Shogun&quot;, &quot;Tapioca Express&quot;, &quot;Burger King&quot;, &quot;KFC&quot;]
[&quot;Piatti&quot;, &quot;The Grill at Torrey Pines&quot;, &quot;Hungry Hunter Steakhouse&quot;, &quot;Shogun&quot;]
<strong>输出:</strong> [&quot;Shogun&quot;]
<strong>解释:</strong> 他们唯一共同喜爱的餐厅是&ldquo;Shogun&rdquo;。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong>
[&quot;Shogun&quot;, &quot;Tapioca Express&quot;, &quot;Burger King&quot;, &quot;KFC&quot;]
[&quot;KFC&quot;, &quot;Shogun&quot;, &quot;Burger King&quot;]
<strong>输出:</strong> [&quot;Shogun&quot;]
<strong>解释:</strong> 他们共同喜爱且具有最小索引和的餐厅是&ldquo;Shogun&rdquo;，它有最小的索引和1(0+1)。
</pre>

<p><strong>提示:</strong></p>

<ol>
	<li>两个列表的长度范围都在&nbsp;[1, 1000]内。</li>
	<li>两个列表中的字符串的长度将在[1，30]的范围内。</li>
	<li>下标从0开始，到列表的长度减1。</li>
	<li>两个列表都没有重复的元素。</li>
</ol>



-----

题目标签：Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/minimum-index-sum-of-two-lists/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-index-sum-of-two-lists/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 92  ms | N/A |

```python3
class Solution:
    def findRestaurant(self, list1, list2):
        """
        :type list1: List[str]
        :type list2: List[str]
        :rtype: List[str]
        """
        d = {}
        for i, r in enumerate(list1):
            if r not in d:
                d[r] = [None, None]
            d[r][0] = i
        for i, r in enumerate(list2):
            if r not in d:
                d[r] = [None, None]
            d[r][1] = i
        dd = []
        for r, ii in d.items():
            if ii[0] is not None and ii[1] is not None:
                dd.append((r, ii[0] + ii[1]))
        dd.sort(key=lambda x: x[1])
        m = dd[0][1]
        res = []
        for r, si in dd:
            if si == m:
                res.append(r)
            else:
                break
        return res
```
