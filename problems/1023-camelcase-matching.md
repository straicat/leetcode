## 1023. Camelcase Matching - 驼峰式匹配

<!--If you want to use the English description, use `question.content` instead-->

<p>如果我们可以将<strong>小写字母</strong>插入模式串&nbsp;<code>pattern</code>&nbsp;得到待查询项&nbsp;<code>query</code>，那么待查询项与给定模式串匹配。（我们可以在任何位置插入每个字符，也可以插入 0 个字符。）</p>

<p>给定待查询列表&nbsp;<code>queries</code>，和模式串&nbsp;<code>pattern</code>，返回由布尔值组成的答案列表&nbsp;<code>answer</code>。只有在待查项&nbsp;<code>queries[i]</code> 与模式串&nbsp;<code>pattern</code> 匹配时，&nbsp;<code>answer[i]</code>&nbsp;才为 <code>true</code>，否则为 <code>false</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>queries = [&quot;FooBar&quot;,&quot;FooBarTest&quot;,&quot;FootBall&quot;,&quot;FrameBuffer&quot;,&quot;ForceFeedBack&quot;], pattern = &quot;FB&quot;
<strong>输出：</strong>[true,false,true,true,false]
<strong>示例：</strong>
&quot;FooBar&quot; 可以这样生成：&quot;F&quot; + &quot;oo&quot; + &quot;B&quot; + &quot;ar&quot;。
&quot;FootBall&quot; 可以这样生成：&quot;F&quot; + &quot;oot&quot; + &quot;B&quot; + &quot;all&quot;.
&quot;FrameBuffer&quot; 可以这样生成：&quot;F&quot; + &quot;rame&quot; + &quot;B&quot; + &quot;uffer&quot;.</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>queries = [&quot;FooBar&quot;,&quot;FooBarTest&quot;,&quot;FootBall&quot;,&quot;FrameBuffer&quot;,&quot;ForceFeedBack&quot;], pattern = &quot;FoBa&quot;
<strong>输出：</strong>[true,false,true,false,false]
<strong>解释：</strong>
&quot;FooBar&quot; 可以这样生成：&quot;Fo&quot; + &quot;o&quot; + &quot;Ba&quot; + &quot;r&quot;.
&quot;FootBall&quot; 可以这样生成：&quot;Fo&quot; + &quot;ot&quot; + &quot;Ba&quot; + &quot;ll&quot;.
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输出：</strong>queries = [&quot;FooBar&quot;,&quot;FooBarTest&quot;,&quot;FootBall&quot;,&quot;FrameBuffer&quot;,&quot;ForceFeedBack&quot;], pattern = &quot;FoBaT&quot;
<strong>输入：</strong>[false,true,false,false,false]
<strong>解释： </strong>
&quot;FooBarTest&quot; 可以这样生成：&quot;Fo&quot; + &quot;o&quot; + &quot;Ba&quot; + &quot;r&quot; + &quot;T&quot; + &quot;est&quot;.
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= queries.length &lt;= 100</code></li>
	<li><code>1 &lt;= queries[i].length &lt;= 100</code></li>
	<li><code>1 &lt;= pattern.length &lt;= 100</code></li>
	<li>所有字符串都仅由大写和小写英文字母组成。</li>
</ol>



-----

题目标签：Trie / String

题目链接：[LeetCode](https://leetcode.com/problems/camelcase-matching/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/camelcase-matching/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 40  ms | 13.3 MB |

```python3
class Solution:
    # 缓存递归中间结果
    cache = None

    def sMatch(self, source, p, pattern, q):
        if __class__.cache[p][q] != -1:
            return __class__.cache[p][q]
        tp, tq = p, q
        if q >= len(pattern):
            # 结束匹配，检查是否还有大写字母未匹配
            while p < len(source):
                if source[p].isupper():
                    return False
                p += 1
            __class__.cache[tp][tq] = 1
            return True
        # 若当前要找的是大写字母
        if pattern[q].isupper():
            while p < len(source) and source[p] != pattern[q]:
                # 如果遇到不同的大写字母，则不匹配
                if source[p].isupper():
                    __class__.cache[tp][tq] = 0
                    return False
                p += 1
            # 如果找不到相应的大写字母
            if p == len(source):
                __class__.cache[tp][tq] = 0
                return False
            # 如果有相应的大写字母，继续向右匹配
            return self.sMatch(source, p + 1, pattern, q + 1)
        # 若当前要找的是小写字母
        else:
            # 找对应的小写字母候选位置
            while p < len(source) and source[p].islower():
                if source[p] == pattern[q]:
                    # 针对每个候选位置继续向右匹配
                    if self.sMatch(source, p + 1, pattern, q + 1):
                        __class__.cache[tp][tq] = 1
                        return True
                p += 1
            __class__.cache[tp][tq] = 0
            return False

    def camelMatch(self, queries: List[str], pattern: str) -> List[bool]:
        res = []
        for source in queries:
            __class__.cache = [[-1] * (len(pattern) + 1)] * (len(source) + 1)
            res.append(self.sMatch(source, 0, pattern, 0))
        return res
```
