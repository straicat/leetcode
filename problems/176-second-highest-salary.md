## 176. Second Highest Salary - 第二高的薪水

<!--If you want to use the English description, use `question.content` instead-->

<p>编写一个 SQL 查询，获取 <code>Employee</code>&nbsp;表中第二高的薪水（Salary）&nbsp;。</p>

<pre>+----+--------+
| Id | Salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
</pre>

<p>例如上述&nbsp;<code>Employee</code>&nbsp;表，SQL查询应该返回&nbsp;<code>200</code> 作为第二高的薪水。如果不存在第二高的薪水，那么查询应返回 <code>null</code>。</p>

<pre>+---------------------+
| SecondHighestSalary |
+---------------------+
| 200                 |
+---------------------+
</pre>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/second-highest-salary/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/second-highest-salary/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| mysql  | 136  ms | N/A |

```mysql
# Write your MySQL query statement below
SELECT MAX(Salary) SecondHighestSalary FROM Employee WHERE Salary<(SELECT MAX(Salary) FROM Employee);
```
