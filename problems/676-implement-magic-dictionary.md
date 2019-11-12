## 676. Implement Magic Dictionary - 实现一个魔法字典

<!--If you want to use the English description, use `question.content` instead-->

<p>实现一个带有<code>buildDict</code>, 以及&nbsp;<code>search</code>方法的魔法字典。</p>

<p>对于<code>buildDict</code>方法，你将被给定一串不重复的单词来构建一个字典。</p>

<p>对于<code>search</code>方法，你将被给定一个单词，并且判定能否只将这个单词中<strong>一个</strong>字母换成另一个字母，使得所形成的新单词存在于你构建的字典中。</p>

<p><strong>示例 1:</strong></p>

<pre>
Input: buildDict([&quot;hello&quot;, &quot;leetcode&quot;]), Output: Null
Input: search(&quot;hello&quot;), Output: False
Input: search(&quot;hhllo&quot;), Output: True
Input: search(&quot;hell&quot;), Output: False
Input: search(&quot;leetcoded&quot;), Output: False
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>你可以假设所有输入都是小写字母&nbsp;<code>a-z</code>。</li>
	<li>为了便于竞赛，测试所用的数据量很小。你可以在竞赛结束后，考虑更高效的算法。</li>
	<li>请记住<strong>重置</strong>MagicDictionary类中声明的类变量，因为静态/类变量会在多个测试用例中保留。 请参阅<a href="http://leetcode.com/faq/#different-output">这里</a>了解更多详情。</li>
</ol>



-----

题目标签：Trie / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/implement-magic-dictionary/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/implement-magic-dictionary/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 60  ms | N/A |

```python3
import string

class MagicDictionary:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.vals = set()

    def buildDict(self, dict):
        """
        Build a dictionary through a list of words
        :type dict: List[str]
        :rtype: void
        """
        for s in dict:
            sl, tmp = list(s), list(s)
            for i in range(len(sl)):
                for c in 'abcdefghijklmnopqrstuvwxyz':
                    if c != sl[i]:
                        tmp[i] = c
                        self.vals.add(''.join(tmp))
                tmp[i] = sl[i]

    def search(self, word):
        """
        Returns if there is any word in the trie that equals to the given word after modifying exactly one character
        :type word: str
        :rtype: bool
        """
        return word in self.vals


# Your MagicDictionary object will be instantiated and called as such:
# obj = MagicDictionary()
# obj.buildDict(dict)
# param_2 = obj.search(word)
```
