## 784. Letter Case Permutation - 字母大小写全排列

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串<code>S</code>，通过将字符串<code>S</code>中的每个字母转变大小写，我们可以获得一个新的字符串。返回所有可能得到的字符串集合。</p>

<pre>
<strong>示例:</strong>
<strong>输入:</strong> S = &quot;a1b2&quot;
<strong>输出:</strong> [&quot;a1b2&quot;, &quot;a1B2&quot;, &quot;A1b2&quot;, &quot;A1B2&quot;]

<strong>输入:</strong> S = &quot;3z4&quot;
<strong>输出:</strong> [&quot;3z4&quot;, &quot;3Z4&quot;]

<strong>输入:</strong> S = &quot;12345&quot;
<strong>输出:</strong> [&quot;12345&quot;]
</pre>

<p><strong>注意：</strong></p>

<ul>
	<li><code>S</code>&nbsp;的长度不超过<code>12</code>。</li>
	<li><code>S</code>&nbsp;仅由数字和字母组成。</li>
</ul>



-----

题目标签：Bit Manipulation / Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/letter-case-permutation/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/letter-case-permutation/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 11  ms | 24.5 MB |

```java
class Solution {
    private void dfs(String s, int i, List<String> res, StringBuffer sb) {
        char c1 = Character.toLowerCase(s.charAt(i));
        char c2 = Character.toUpperCase(s.charAt(i));
        if (i == s.length() - 1) {
            sb.append(c1);
            res.add(sb.toString());
            sb.deleteCharAt(sb.length()-1);
            if (c1 != c2) {
                sb.append(c2);
                res.add(sb.toString());
                sb.deleteCharAt(sb.length()-1);
            }
        } else {
            sb.append(c1);
            dfs(s, i+1, res, sb);
            sb.deleteCharAt(sb.length()-1);
            if (c1 != c2) {
                sb.append(c2);
                dfs(s, i+1, res, sb);
                sb.deleteCharAt(sb.length()-1);
            }
        }
    }
    public List<String> letterCasePermutation(String S) {
        List<String> res = new ArrayList<String>();
        if (S.length() == 0) {
            res.add(S);
            return res;
        }
        StringBuffer sb = new StringBuffer();
        dfs(S, 0, res, sb);
        return res;
    }
}
```
