## 528. Random Pick with Weight - 按权重随机选择

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个正整数数组&nbsp;<code>w</code> ，其中&nbsp;<code>w[i]</code>&nbsp;代表位置&nbsp;<code>i</code>&nbsp;的权重，请写一个函数&nbsp;<code>pickIndex</code>&nbsp;，它可以随机地获取位置&nbsp;<code>i</code>，选取位置&nbsp;<code>i</code>&nbsp;的概率与&nbsp;<code>w[i]</code>&nbsp;成正比。</p>

<p>说明:</p>

<ol>
	<li><code>1 &lt;= w.length &lt;= 10000</code></li>
	<li><code>1 &lt;= w[i] &lt;= 10^5</code></li>
	<li><code>pickIndex</code>&nbsp;将被调用不超过&nbsp;<code>10000</code>&nbsp;次</li>
</ol>

<p><strong>示例1:</strong></p>

<pre>
<strong>输入: 
</strong>[&quot;Solution&quot;,&quot;pickIndex&quot;]
[[[1]],[]]
<strong>输出: </strong>[null,0]
</pre>

<p><strong>示例2:</strong></p>

<pre>
<strong>输入: 
</strong>[&quot;Solution&quot;,&quot;pickIndex&quot;,&quot;pickIndex&quot;,&quot;pickIndex&quot;,&quot;pickIndex&quot;,&quot;pickIndex&quot;]
[[[1,3]],[],[],[],[],[]]
<strong>输出: </strong>[null,0,1,1,1,0]</pre>

<p><strong>输入语法说明：</strong></p>

<p>输入是两个列表：调用成员函数名和调用的参数。<code>Solution</code>&nbsp;的构造函数有一个参数，即数组&nbsp;<code>w</code>。<code>pickIndex</code>&nbsp;没有参数。输入参数是一个列表，即使参数为空，也会输入一个 [] 空列表。</p>



-----

题目标签：Binary Search / Random

题目链接：[LeetCode](https://leetcode.com/problems/random-pick-with-weight/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/random-pick-with-weight/description/)

## 题解

![OJ草稿-12](https://user-images.githubusercontent.com/9983385/55524600-7cdbcd00-56c0-11e9-86d0-3fcfa526d41f.jpg)

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 67  ms | 48.3 MB |

```java
class Solution {

    private int[] w;
    private int[] s;
    public Solution(int[] w) {
        this.w = w;
        s = w;
        int tmp = 0;
        for (int i = 0; i < w.length; i++) {
            tmp += w[i];
            s[i] = tmp;
        }
    }

    public int pickIndex() {
        int t = (int)(Math.random() * s[s.length - 1]) + 1;
        int l = 0, r = s.length - 1;
        while (l < r) {
            int mid = l + r >> 1;
            if (s[mid] >= t) r = mid;
            else l = mid + 1;
        }
        return l;
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(w);
 * int param_1 = obj.pickIndex();
 */
```
