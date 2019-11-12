## 183. Customers Who Never Order - 从不订购的客户

<!--If you want to use the English description, use `question.content` instead-->

<p>某网站包含两个表，<code>Customers</code> 表和 <code>Orders</code> 表。编写一个 SQL 查询，找出所有从不订购任何东西的客户。</p>

<p><code>Customers</code> 表：</p>

<pre>+----+-------+
| Id | Name  |
+----+-------+
| 1  | Joe   |
| 2  | Henry |
| 3  | Sam   |
| 4  | Max   |
+----+-------+
</pre>

<p><code>Orders</code> 表：</p>

<pre>+----+------------+
| Id | CustomerId |
+----+------------+
| 1  | 3          |
| 2  | 1          |
+----+------------+
</pre>

<p>例如给定上述表格，你的查询应返回：</p>

<pre>+-----------+
| Customers |
+-----------+
| Henry     |
| Max       |
+-----------+
</pre>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/customers-who-never-order/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/customers-who-never-order/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| mysql  | 263  ms | N/A |

```mysql
# Write your MySQL query statement below
SELECT Name Customers
FROM Customers C
LEFT JOIN Orders O
ON C.Id = O.CustomerId
WHERE CustomerId IS NULL;
```
