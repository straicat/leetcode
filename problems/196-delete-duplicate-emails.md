## 196. Delete Duplicate Emails - 删除重复的电子邮箱

<!--If you want to use the English description, use `question.content` instead-->

<p>编写一个 SQL 查询，来删除&nbsp;<code>Person</code>&nbsp;表中所有重复的电子邮箱，重复的邮箱里只保留&nbsp;<strong>Id&nbsp;</strong><em>最小&nbsp;</em>的那个。</p>

<pre>+----+------------------+
| Id | Email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
| 3  | john@example.com |
+----+------------------+
Id 是这个表的主键。
</pre>

<p>例如，在运行你的查询语句之后，上面的 <code>Person</code> 表应返回以下几行:</p>

<pre>+----+------------------+
| Id | Email            |
+----+------------------+
| 1  | john@example.com |
| 2  | bob@example.com  |
+----+------------------+
</pre>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/delete-duplicate-emails/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/delete-duplicate-emails/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| mysql  | 528  ms | N/A |

```mysql
# Write your MySQL query statement below
DELETE FROM Person WHERE Id NOT IN (
    SELECT t.Id FROM(
        SELECT MIN(Id) Id FROM Person GROUP BY Email
    ) t
);
```
