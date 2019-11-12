## 139. Word Break - 单词拆分

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个<strong>非空</strong>字符串 <em>s</em> 和一个包含<strong>非空</strong>单词列表的字典 <em>wordDict</em>，判定&nbsp;<em>s</em> 是否可以被空格拆分为一个或多个在字典中出现的单词。</p>

<p><strong>说明：</strong></p>

<ul>
	<li>拆分时可以重复使用字典中的单词。</li>
	<li>你可以假设字典中没有重复的单词。</li>
</ul>

<p><strong>示例 1：</strong></p>

<pre><strong>输入:</strong> s = &quot;leetcode&quot;, wordDict = [&quot;leet&quot;, &quot;code&quot;]
<strong>输出:</strong> true
<strong>解释:</strong> 返回 true 因为 &quot;leetcode&quot; 可以被拆分成 &quot;leet code&quot;。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入:</strong> s = &quot;applepenapple&quot;, wordDict = [&quot;apple&quot;, &quot;pen&quot;]
<strong>输出:</strong> true
<strong>解释:</strong> 返回 true 因为 <code>&quot;</code>applepenapple<code>&quot;</code> 可以被拆分成 <code>&quot;</code>apple pen apple<code>&quot;</code>。
&nbsp;    注意你可以重复使用字典中的单词。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入:</strong> s = &quot;catsandog&quot;, wordDict = [&quot;cats&quot;, &quot;dog&quot;, &quot;sand&quot;, &quot;and&quot;, &quot;cat&quot;]
<strong>输出:</strong> false
</pre>



-----

题目标签：Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/word-break/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/word-break/description/)

## 题解

一开始想到递归，果不其然，TLE。

然后改成记忆化递归，结果因为用了类变量，而LeetCode是同一实例重复调用方法，结果出错。

于是，定义个函数用于递归，就解决了上面的问题。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | N/A |

```python3
class Solution:
    def wordBreak(self, s, wordDict):
        """
        :type s: str
        :type wordDict: List[str]
        :rtype: bool
        """
        cache = {}
        def warpper(_s, _wordDict):
            if _s in cache:
                return cache[_s]
            for w in _wordDict:
                if _s == w:
                    cache[_s] = True
                    return True
                elif _s.startswith(w):
                    if warpper(_s[len(w):], _wordDict):
                        cache[_s] = True
                        return True
            cache[_s] = False
            return False
        return warpper(s, wordDict)
```
