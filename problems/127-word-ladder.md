## 127. Word Ladder - 单词接龙

<!--If you want to use the English description, use `question.content` instead-->

<p>给定两个单词（<em>beginWord&nbsp;</em>和 <em>endWord</em>）和一个字典，找到从&nbsp;<em>beginWord</em> 到&nbsp;<em>endWord</em> 的最短转换序列的长度。转换需遵循如下规则：</p>

<ol>
	<li>每次转换只能改变一个字母。</li>
	<li>转换过程中的中间单词必须是字典中的单词。</li>
</ol>

<p><strong>说明:</strong></p>

<ul>
	<li>如果不存在这样的转换序列，返回 0。</li>
	<li>所有单词具有相同的长度。</li>
	<li>所有单词只由小写字母组成。</li>
	<li>字典中不存在重复的单词。</li>
	<li>你可以假设 <em>beginWord</em> 和 <em>endWord </em>是非空的，且二者不相同。</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong>
beginWord = &quot;hit&quot;,
endWord = &quot;cog&quot;,
wordList = [&quot;hot&quot;,&quot;dot&quot;,&quot;dog&quot;,&quot;lot&quot;,&quot;log&quot;,&quot;cog&quot;]

<strong>输出: </strong>5

<strong>解释: </strong>一个最短转换序列是 &quot;hit&quot; -&gt; &quot;hot&quot; -&gt; &quot;dot&quot; -&gt; &quot;dog&quot; -&gt; &quot;cog&quot;,
     返回它的长度 5。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong>
beginWord = &quot;hit&quot;
endWord = &quot;cog&quot;
wordList = [&quot;hot&quot;,&quot;dot&quot;,&quot;dog&quot;,&quot;lot&quot;,&quot;log&quot;]

<strong>输出:</strong>&nbsp;0

<strong>解释:</strong>&nbsp;<em>endWord</em> &quot;cog&quot; 不在字典中，所以无法进行转换。</pre>



-----

题目标签：Breadth-first Search

题目链接：[LeetCode](https://leetcode.com/problems/word-ladder/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/word-ladder/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 340  ms | 1.8 MB |

```cpp
static auto _ = [](){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();

class Solution {
public:
    bool diffone(string& s1, string& s2) {
        int res = 0;
        for (int i=0; i<(int)s1.size(); ++i) {
            if (s1[i] != s2[i]) {
                if (1 < ++res) {
                    return false;
                }
            }
        }
        return res == 1;
    }
    int ladderLength(string beginWord, string endWord, vector<string>& wordList) {
        queue<string> Q;
        unordered_set<string> avail;
        avail.insert(wordList.begin(), wordList.end());
        int res = 0;
        Q.push(beginWord);
        avail.erase(beginWord);
        vector<string> del;
        while (!Q.empty()) {
            int n = Q.size();
            res++;
            while (n--) {
                string tmp = Q.front();
                Q.pop();
                del.clear();
                for (auto s : avail) {
                    if (diffone(s, tmp)) {
                        if (s == endWord) {
                            return res + 1;
                        }
                        Q.push(s);
                        del.push_back(s);
                    }
                }
                for (auto s : del) {
                    avail.erase(s);
                }
            }
        }
        return 0;
    }
};
```
