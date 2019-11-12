## 412. Fizz Buzz - Fizz Buzz

<!--If you want to use the English description, use `question.content` instead-->

<p>写一个程序，输出从 1 到 <em>n</em> 数字的字符串表示。</p>

<p>1. 如果&nbsp;<em>n&nbsp;</em>是3的倍数，输出&ldquo;Fizz&rdquo;；</p>

<p>2. 如果&nbsp;<em>n&nbsp;</em>是5的倍数，输出&ldquo;Buzz&rdquo;；</p>

<p>3.如果&nbsp;<em>n&nbsp;</em>同时是3和5的倍数，输出 &ldquo;FizzBuzz&rdquo;。</p>

<p><strong>示例：</strong></p>

<pre>n = 15,

返回:
[
    &quot;1&quot;,
    &quot;2&quot;,
    &quot;Fizz&quot;,
    &quot;4&quot;,
    &quot;Buzz&quot;,
    &quot;Fizz&quot;,
    &quot;7&quot;,
    &quot;8&quot;,
    &quot;Fizz&quot;,
    &quot;Buzz&quot;,
    &quot;11&quot;,
    &quot;Fizz&quot;,
    &quot;13&quot;,
    &quot;14&quot;,
    &quot;FizzBuzz&quot;
]
</pre>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/fizz-buzz/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/fizz-buzz/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 1  ms | 38.3 MB |

```java
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> res = new ArrayList<>();
        for (int i = 1; i <= n; i++) {
            if (i %  3 == 0 && i % 5 == 0) {
                res.add("FizzBuzz");
            } else {
                if (i % 3 == 0) {
                    res.add("Fizz");
                } else if (i % 5 == 0) {
                    res.add("Buzz");
                } else {
                    res.add(String.valueOf(i));
                }
            }
        }
        return res;
    }
}
```
