## 459. Repeated Substring Pattern - 重复的子字符串

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个非空的字符串，判断它是否可以由它的一个子串重复多次构成。给定的字符串只含有小写英文字母，并且长度不超过10000。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> &quot;abab&quot;

<strong>输出:</strong> True

<strong>解释:</strong> 可由子字符串 &quot;ab&quot; 重复两次构成。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> &quot;aba&quot;

<strong>输出:</strong> False
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> &quot;abcabcabcabc&quot;

<strong>输出:</strong> True

<strong>解释:</strong> 可由子字符串 &quot;abc&quot; 重复四次构成。 (或者子字符串 &quot;abcabc&quot; 重复两次构成。)
</pre>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/repeated-substring-pattern/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/repeated-substring-pattern/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 30  ms | N/A |

```java
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        for(int i=2; i<=s.length(); i++){
            if(s.length()%i!=0)
                continue;
            int a = s.length()/i;
            String s1 = s.substring(0, a);
            boolean flag = true;
            for(int j=2; j<=s.length()/a; j++){
                String tmp = s.substring((j-1)*a, j*a);
                if(!tmp.equals(s1)){
                    flag = false;
                    break;
                }
            }
            if(flag)
                return true;
        }
        return false;
    }
}
```
