## 168. Excel Sheet Column Title - Excel表列名称

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个正整数，返回它在 Excel 表中相对应的列名称。</p>

<p>例如，</p>

<pre>    1 -&gt; A
    2 -&gt; B
    3 -&gt; C
    ...
    26 -&gt; Z
    27 -&gt; AA
    28 -&gt; AB 
    ...
</pre>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 1
<strong>输出:</strong> &quot;A&quot;
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> 28
<strong>输出:</strong> &quot;AB&quot;
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入:</strong> 701
<strong>输出:</strong> &quot;ZY&quot;
</pre>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/excel-sheet-column-title/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/excel-sheet-column-title/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 0  ms | 35.3 MB |

```java
class Solution {
    public String convertToTitle(int n) {
        StringBuilder sb = new StringBuilder();
        String s = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        while (n > 0) {
            sb.append(s.charAt((n - 1) % 26));
            n = (n - 1) / 26;
        }
        return sb.reverse().toString();
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 852 KB |

```cpp
class Solution {
public:
    string convertToTitle(int n) {
        string alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        string res;
        /*
        A-Z  1-26
        AA 27 26+1  26*1+1
        AB 28 26+2  26*1+2
        AZ    26*1+26
        BA    26*2+1
        BB    26*2+2
        ZY    26*26+25
        ZZ    26*26+26
        AAA   26*26*1+26*1+1
        */
        while (n) {
            if (n % 26 == 0) {
                res = 'Z' + res;
                n = n / 26 - 1;
            } else {
                res = alphabet[n % 26 - 1] + res;
                n /= 26;
            }
        }
        return res;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
