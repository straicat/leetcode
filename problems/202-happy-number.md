## 202. Happy Number - 快乐数

<!--If you want to use the English description, use `question.content` instead-->

<p>编写一个算法来判断一个数是不是&ldquo;快乐数&rdquo;。</p>

<p>一个&ldquo;快乐数&rdquo;定义为：对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和，然后重复这个过程直到这个数变为 1，也可能是无限循环但始终变不到 1。如果可以变为 1，那么这个数就是快乐数。</p>

<p><strong>示例:&nbsp;</strong></p>

<pre><strong>输入:</strong> 19
<strong>输出:</strong> true
<strong>解释: 
</strong>1<sup>2</sup> + 9<sup>2</sup> = 82
8<sup>2</sup> + 2<sup>2</sup> = 68
6<sup>2</sup> + 8<sup>2</sup> = 100
1<sup>2</sup> + 0<sup>2</sup> + 0<sup>2</sup> = 1
</pre>



-----

题目标签：Hash Table / Math

题目链接：[LeetCode](https://leetcode.com/problems/happy-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/happy-number/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 84  ms | N/A |

```python3
class Solution:
    def isHappy(self, n):
        """
        :type n: int
        :rtype: bool
        """
        num = n
        tmp = {}
        while True:
            num = self.calc(num)
            if num == 1:
                return True
            else:
                if num in tmp:
                    return False
                else:
                    tmp[num] = 0

    def calc(self, n):
        t = list(map(int, list(str(n))))
        res = sum(list(map(lambda x: x ** 2, t)))
        # tt = list(map(lambda x: '%s^2' % str(x), t))
        # print(' + '.join(tt) + ' = ' + str(res))
        return res
```
