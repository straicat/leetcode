## 596. Classes More Than 5 Students - 超过5名学生的课

<!--If you want to use the English description, use `question.content` instead-->

<p>有一个<code>courses</code> 表 ，有: <strong>student&nbsp;(学生) </strong>和 <strong>class (课程)</strong>。</p>

<p>请列出所有超过或等于5名学生的课。</p>

<p>例如,表:</p>

<pre>
+---------+------------+
| student | class      |
+---------+------------+
| A       | Math       |
| B       | English    |
| C       | Math       |
| D       | Biology    |
| E       | Math       |
| F       | Computer   |
| G       | Math       |
| H       | Math       |
| I       | Math       |
+---------+------------+
</pre>

<p>应该输出:</p>

<pre>
+---------+
| class   |
+---------+
| Math    |
+---------+
</pre>

<p><strong>Note:</strong><br />
学生在每个课中不应被重复计算。</p>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/classes-more-than-5-students/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/classes-more-than-5-students/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| mysql  | 1548  ms | N/A |

```mysql
# Write your MySQL query statement below
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(DISTINCT student) > 4;
```
