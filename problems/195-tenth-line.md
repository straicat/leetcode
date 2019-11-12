## 195. Tenth Line - 第十行

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个文本文件&nbsp;<code>file.txt</code>，请只打印这个文件中的第十行。</p>

<p><strong>示例:</strong></p>

<p>假设&nbsp;<code>file.txt</code> 有如下内容：</p>

<pre>Line 1
Line 2
Line 3
Line 4
Line 5
Line 6
Line 7
Line 8
Line 9
Line 10
</pre>

<p>你的脚本应当显示第十行：</p>

<pre>Line 10
</pre>

<p><strong>说明:</strong><br>
1. 如果文件少于十行，你应当输出什么？<br>
2. 至少有三种不同的解法，请尝试尽可能多的方法来解题。</p>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/tenth-line/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/tenth-line/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| bash  | 4  ms | N/A |

```bash
# Read from the file file.txt and output the tenth line to stdout.
sed -n '10p' file.txt
```
