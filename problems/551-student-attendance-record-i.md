## 551. Student Attendance Record I - 学生出勤记录 I

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串来代表一个学生的出勤记录，这个记录仅包含以下三个字符：</p>

<ol>
	<li><strong>&#39;A&#39;</strong> : Absent，缺勤</li>
	<li><strong>&#39;L&#39;</strong> : Late，迟到</li>
	<li><strong>&#39;P&#39;</strong> : Present，到场</li>
</ol>

<p>如果一个学生的出勤记录中不<strong>超过一个&#39;A&#39;(缺勤)</strong>并且<strong>不超过两个连续的&#39;L&#39;(迟到)</strong>,那么这个学生会被奖赏。</p>

<p>你需要根据这个学生的出勤记录判断他是否会被奖赏。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> &quot;PPALLP&quot;
<strong>输出:</strong> True
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> &quot;PPALLL&quot;
<strong>输出:</strong> False
</pre>



-----

题目标签：String

题目链接：[LeetCode](https://leetcode.com/problems/student-attendance-record-i/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/student-attendance-record-i/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | N/A |

```python3
class Solution:
    def checkRecord(self, s):
        """
        :type s: str
        :rtype: bool
        """
        if s.count('A') > 1 or 'LLL' in s:
            return False
        return True
```
