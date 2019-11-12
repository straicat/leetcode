## 3. Longest Substring Without Repeating Characters - 无重复字符的最长子串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串，请你找出其中不含有重复字符的&nbsp;<strong>最长子串&nbsp;</strong>的长度。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入: </strong>&quot;abcabcbb&quot;
<strong>输出: </strong>3 
<strong>解释:</strong> 因为无重复字符的最长子串是 <code>&quot;abc&quot;，所以其</code>长度为 3。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong>&quot;bbbbb&quot;
<strong>输出: </strong>1
<strong>解释: </strong>因为无重复字符的最长子串是 <code>&quot;b&quot;</code>，所以其长度为 1。
</pre>

<p><strong>示例 3:</strong></p>

<pre><strong>输入: </strong>&quot;pwwkew&quot;
<strong>输出: </strong>3
<strong>解释: </strong>因为无重复字符的最长子串是&nbsp;<code>&quot;wke&quot;</code>，所以其长度为 3。
&nbsp;    请注意，你的答案必须是 <strong>子串 </strong>的长度，<code>&quot;pwke&quot;</code>&nbsp;是一个<em>子序列，</em>不是子串。
</pre>



-----

题目标签：Hash Table / Two Pointers / String / Sliding Window

题目链接：[LeetCode](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 23  ms | 39.3 MB |

```java
public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        int res = 0;
        HashMap<Character, Integer> map = new HashMap<>();
        for (int i = 0, j = 0; j < n; j++) {
            if (map.containsKey(s.charAt(j)) && map.get(s.charAt(j)) >= i) {
                i = map.get(s.charAt(j)) + 1;
            }
            map.put(s.charAt(j), j);
            res = Math.max(res, j - i + 1);
        }
        return res;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 20  ms | N/A |

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int res = 0;
        deque<char> sub;
        unordered_set<char> look;
        for(char c : s){
            if(look.count(c)){
                res = max(res, (int)sub.size());
                while(true){
                    char b = sub.front();
                    sub.pop_front();
                    look.erase(b);
                    if(b == c){
                        break;
                    }
                }
            }
            sub.push_back(c);
            look.insert(c);
        }
        res = max(res, (int)sub.size());
        return res;
    }
};
```
