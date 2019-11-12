## 911. Online Election - 在线选举

<!--If you want to use the English description, use `question.content` instead-->

<p>在选举中，第&nbsp;<code>i</code>&nbsp;张票是在时间为&nbsp;<code>times[i]</code>&nbsp;时投给&nbsp;<code>persons[i]</code>&nbsp;的。</p>

<p>现在，我们想要实现下面的查询函数： <code>TopVotedCandidate.q(int t)</code> 将返回在&nbsp;<code>t</code> 时刻主导选举的候选人的编号。</p>

<p>在&nbsp;<code>t</code> 时刻投出的选票也将被计入我们的查询之中。在平局的情况下，最近获得投票的候选人将会获胜。</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[&quot;TopVotedCandidate&quot;,&quot;q&quot;,&quot;q&quot;,&quot;q&quot;,&quot;q&quot;,&quot;q&quot;,&quot;q&quot;], [[[0,1,1,0,0,1,0],[0,5,10,15,20,25,30]],[3],[12],[25],[15],[24],[8]]
<strong>输出：</strong>[null,0,1,1,0,0,1]
<strong>解释：</strong>
时间为 3，票数分布情况是 [0]，编号为 0 的候选人领先。
时间为 12，票数分布情况是 [0,1,1]，编号为 1 的候选人领先。
时间为 25，票数分布情况是 [0,1,1,0,0,1]，编号为 1 的候选人领先（因为最近的投票结果是平局）。
在时间 15、24 和 8 处继续执行 3 个查询。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= persons.length = times.length &lt;= 5000</code></li>
	<li><code>0 &lt;= persons[i] &lt;= persons.length</code></li>
	<li><code>times</code>&nbsp;是严格递增的数组，所有元素都在&nbsp;<code>[0, 10^9]</code>&nbsp;范围中。</li>
	<li>每个测试用例最多调用&nbsp;<code>10000</code>&nbsp;次&nbsp;<code>TopVotedCandidate.q</code>。</li>
	<li><code>TopVotedCandidate.q(int t)</code>&nbsp;被调用时总是满足&nbsp;<code>t &gt;= times[0]</code>。</li>
</ol>



-----

题目标签：Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/online-election/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/online-election/description/)

## 题解

比较简单，主要是要理解题意。

某次投票后到下次投票前，投票结果不变。因此，可以记录每次投票后的投票结果，然后查询时利用二分法定位，直接取之前最近一次的投票结果即可。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 408  ms | N/A |

```python3
class TopVotedCandidate:

    def __init__(self, persons, times):
        """
        :type persons: List[int]
        :type times: List[int]
        """
        self.res = collections.OrderedDict()
        c = collections.defaultdict(int)
        best = {'person': None, 'vote': 0}
        for p, t in zip(persons, times):
            c[p] += 1
            if c[p] >= best['vote']:
                best['person'] = p
                best['vote'] = c[p]
            self.res[t] = best['person']
            # print(best)
        # print(self.res)
        self.res_keys = list(self.res.keys())

    def q(self, t):
        """
        :type t: int
        :rtype: int
        """
        # print(t, bisect.bisect_right(self.res_keys, t)-1)
        return self.res[self.res_keys[bisect.bisect_right(self.res_keys, t)-1]]


# Your TopVotedCandidate object will be instantiated and called as such:
# obj = TopVotedCandidate(persons, times)
# param_1 = obj.q(t)
```
