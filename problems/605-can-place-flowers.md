## 605. Can Place Flowers - 种花问题

<!--If you want to use the English description, use `question.content` instead-->

<p>假设你有一个很长的花坛，一部分地块种植了花，另一部分却没有。可是，花卉不能种植在相邻的地块上，它们会争夺水源，两者都会死去。</p>

<p>给定一个花坛（表示为一个数组包含0和1，其中0表示没种植花，1表示种植了花），和一个数&nbsp;<strong>n&nbsp;</strong>。能否在不打破种植规则的情况下种入&nbsp;<strong>n&nbsp;</strong>朵花？能则返回True，不能则返回False。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> flowerbed = [1,0,0,0,1], n = 1
<strong>输出:</strong> True
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> flowerbed = [1,0,0,0,1], n = 2
<strong>输出:</strong> False
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>数组内已种好的花不会违反种植规则。</li>
	<li>输入的数组长度范围为 [1, 20000]。</li>
	<li><strong>n</strong> 是非负整数，且不会超过输入数组的大小。</li>
</ol>



-----

题目标签：Array

题目链接：[LeetCode](https://leetcode.com/problems/can-place-flowers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/can-place-flowers/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 124  ms | N/A |

```python3
class Solution:
    def canPlaceFlowers(self, flowerbed, n):
        """
        :type flowerbed: List[int]
        :type n: int
        :rtype: bool
        """
        if n == 0:
            return True
        fl = [0]
        fl.extend(flowerbed)
        fl.append(0)
        num = 0
        for i in range(1, len(fl)-1):
            if not any([fl[i+j] for j in (-1, 0, 1)]):
                fl[i] = 1
                num += 1
                if num >= n:
                    return True
        return False
```
