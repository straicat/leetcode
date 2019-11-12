## 175. Combine Two Tables - 组合两个表

<!--If you want to use the English description, use `question.content` instead-->

<p>表1: <code>Person</code></p>

<pre>+-------------+---------+
| 列名         | 类型     |
+-------------+---------+
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |
+-------------+---------+
PersonId 是上表主键
</pre>

<p>表2: <code>Address</code></p>

<pre>+-------------+---------+
| 列名         | 类型    |
+-------------+---------+
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |
+-------------+---------+
AddressId 是上表主键
</pre>

<p>&nbsp;</p>

<p>编写一个 SQL 查询，满足条件：无论 person 是否有地址信息，都需要基于上述两表提供&nbsp;person 的以下信息：</p>

<p>&nbsp;</p>

<pre>FirstName, LastName, City, State
</pre>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/combine-two-tables/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/combine-two-tables/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| mysql  | 216  ms | N/A |

```mysql
SELECT FirstName, LastName, City, State FROM Person p LEFT JOIN Address a ON p.PersonId=a.PersonId;
```
