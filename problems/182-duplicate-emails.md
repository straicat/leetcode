## 182. Duplicate Emails - 查找重复的电子邮箱

<!--If you want to use the English description, use `question.content` instead-->

<p>编写一个 SQL 查询，查找&nbsp;<code>Person</code> 表中所有重复的电子邮箱。</p>

<p><strong>示例：</strong></p>

<pre>+----+---------+
| Id | Email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+
</pre>

<p>根据以上输入，你的查询应返回以下结果：</p>

<pre>+---------+
| Email   |
+---------+
| a@b.com |
+---------+
</pre>

<p><strong>说明：</strong>所有电子邮箱都是小写字母。</p>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/duplicate-emails/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/duplicate-emails/description/)

## 题解

在用子查询时：

Every derived table must have its own alias

原因：要给子表取个别名。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| mysql  | 401  ms | N/A |

```mysql
SELECT Email FROM (SELECT Email, COUNT(Email) c FROM Person GROUP BY Email) t WHERE t.c>1;
```
