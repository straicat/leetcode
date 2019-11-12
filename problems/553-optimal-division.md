## 553. Optimal Division - 最优除法

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一组<strong>正整数，</strong>相邻的整数之间将会进行浮点除法操作。例如，&nbsp;[2,3,4] -&gt; 2 / 3 / 4 。</p>

<p>但是，你可以在任意位置添加任意数目的括号，来改变算数的优先级。你需要找出怎么添加括号，才能得到<strong>最大的</strong>结果，并且返回相应的字符串格式的表达式。<strong>你的表达式不应该含有冗余的括号。</strong></p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入:</strong> [1000,100,10,2]
<strong>输出:</strong> &quot;1000/(100/10/2)&quot;
<strong>解释:</strong>
1000/(100/10/2) = 1000/((100/10)/2) = 200
但是，以下加粗的括号 &quot;1000/(<strong>(</strong>100/10<strong>)</strong>/2)&quot; 是冗余的，
因为他们并不影响操作的优先级，所以你需要返回 &quot;1000/(100/10/2)&quot;。

其他用例:
1000/(100/10)/2 = 50
1000/(100/(10/2)) = 50
1000/100/10/2 = 0.5
1000/100/(10/2) = 2
</pre>

<p><strong>说明:</strong></p>

<ol>
	<li>输入数组的长度在 [1, 10] 之间。</li>
	<li>数组中每个元素的大小都在 [2, 1000] 之间。</li>
	<li>每个测试用例只有一个最优除法解。</li>
</ol>



-----

题目标签：Math / String

题目链接：[LeetCode](https://leetcode.com/problems/optimal-division/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/optimal-division/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 32  ms | N/A |

```python3
class Solution:
    def optimalDivision(self, nums):
        """
        :type nums: List[int]
        :rtype: str
        """
        if len(nums) == 1:
            return str(nums[0])
        elif len(nums) == 2:
            return '%d/%d' % (nums[0], nums[1])
        else:
            return '%d/(' % nums[0] + '/'.join(map(str, nums[1:])) + ')'
```
