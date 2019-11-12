## 181. Employees Earning More Than Their Managers - 超过经理收入的员工

<!--If you want to use the English description, use `question.content` instead-->

<p><code>Employee</code>&nbsp;表包含所有员工，他们的经理也属于员工。每个员工都有一个 Id，此外还有一列对应员工的经理的 Id。</p>

<pre>+----+-------+--------+-----------+
| Id | Name  | Salary | ManagerId |
+----+-------+--------+-----------+
| 1  | Joe   | 70000  | 3         |
| 2  | Henry | 80000  | 4         |
| 3  | Sam   | 60000  | NULL      |
| 4  | Max   | 90000  | NULL      |
+----+-------+--------+-----------+
</pre>

<p>给定&nbsp;<code>Employee</code>&nbsp;表，编写一个 SQL 查询，该查询可以获取收入超过他们经理的员工的姓名。在上面的表格中，Joe 是唯一一个收入超过他的经理的员工。</p>

<pre>+----------+
| Employee |
+----------+
| Joe      |
+----------+
</pre>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/employees-earning-more-than-their-managers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/employees-earning-more-than-their-managers/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| mysql  | 298  ms | N/A |

```mysql
SELECT e1.Name Employee FROM Employee e1 JOIN (SELECT * FROM Employee) e2 ON e1.ManagerId=e2.id WHERE e1.Salary > e2.Salary;
```
