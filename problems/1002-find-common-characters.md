## 1002. Find Common Characters - 查找常用字符

<!--If you want to use the English description, use `question.content` instead-->

<p>给定仅有小写字母组成的字符串数组 <code>A</code>，返回列表中的每个字符串中都显示的全部字符（<strong>包括重复字符</strong>）组成的列表。例如，如果一个字符在每个字符串中出现 3 次，但不是 4 次，则需要在最终答案中包含该字符 3 次。</p>

<p>你可以按任意顺序返回答案。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[&quot;bella&quot;,&quot;label&quot;,&quot;roller&quot;]
<strong>输出：</strong>[&quot;e&quot;,&quot;l&quot;,&quot;l&quot;]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[&quot;cool&quot;,&quot;lock&quot;,&quot;cook&quot;]
<strong>输出：</strong>[&quot;c&quot;,&quot;o&quot;]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 100</code></li>
	<li><code>1 &lt;= A[i].length &lt;= 100</code></li>
	<li><code>A[i][j]</code> 是小写字母</li>
</ol>



-----

题目标签：Array / Hash Table

题目链接：[LeetCode](https://leetcode.com/problems/find-common-characters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-common-characters/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 8  ms | 40.6 MB |

```java
class Solution {
    public List<String> commonChars(String[] A) {
        int[][] rec = new int[26][A.length];
        for (int i = 0; i < A.length; i++) {
            for (int j = 0; j < A[i].length(); j++) {
                rec[A[i].charAt(j) - 'a'][i]++;
            }
        }
        List<String> res = new ArrayList<>();
        for (int i = 0; i < 26; i++) {
            Arrays.sort(rec[i]);
            int j = rec[i][0];
            for (int k = 0; k < j; k++) {
                res.add(new Character((char)('a' + i)).toString());
            }
        }
        return res;
    }
}
```
