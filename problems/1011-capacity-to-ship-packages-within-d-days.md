## 1011. Capacity To Ship Packages Within D Days - 在 D 天内送达包裹的能力

<!--If you want to use the English description, use `question.content` instead-->

<p>传送带上的包裹必须在 D 天内从一个港口运送到另一个港口。</p>

<p>传送带上的第 <code>i</code>&nbsp;个包裹的重量为&nbsp;<code>weights[i]</code>。每一天，我们都会按给出重量的顺序往传送带上装载包裹。我们装载的重量不会超过船的最大运载重量。</p>

<p>返回能在 <code>D</code> 天内将传送带上的所有包裹送达的船的最低运载能力。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>weights = [1,2,3,4,5,6,7,8,9,10], D = 5
<strong>输出：</strong>15
<strong>解释：</strong>
船舶最低载重 15 就能够在 5 天内送达所有包裹，如下所示：
第 1 天：1, 2, 3, 4, 5
第 2 天：6, 7
第 3 天：8
第 4 天：9
第 5 天：10

请注意，货物必须按照给定的顺序装运，因此使用载重能力为 14 的船舶并将包装分成 (2, 3, 4, 5), (1, 6, 7), (8), (9), (10) 是不允许的。 
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>weights = [3,2,2,4,1,4], D = 3
<strong>输出：</strong>6
<strong>解释：</strong>
船舶最低载重 6 就能够在 3 天内送达所有包裹，如下所示：
第 1 天：3, 2
第 2 天：2, 4
第 3 天：1, 4
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>weights = [1,2,3,1,1], D = 4
<strong>输出：</strong>3
<strong>解释：</strong>
第 1 天：1
第 2 天：2
第 3 天：3
第 4 天：1, 1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= D &lt;= weights.length &lt;= 50000</code></li>
	<li><code>1 &lt;= weights[i] &lt;= 500</code></li>
</ol>



-----

题目标签：Array / Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/capacity-to-ship-packages-within-d-days/description/)

## 题解

Similar as

875. Koko Eating Bananas

774. Minimize Max Distance to Gas Station



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 52  ms | 11.9 MB |

```cpp
class Solution {
public:
    int shipWithinDays(vector<int>& weights, int D) {
        int left = *max_element(weights.begin(), weights.end());
        int right = accumulate(weights.begin(), weights.end(), 0);
        while (left < right) {
            int mid = left + right >> 1;
            int t = 0;
            int d = 1; // 注意这里天数的初值
            for (int w : weights) {
                if (t + w > mid) {
                    d++;
                    if (d > D) break;
                    t = 0;
                }
                t += w;
            }
            if (d <= D) right = mid;
            else left = mid + 1;
        }
        return left;
    }
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 388  ms | 15.2 MB |

```python3
class Solution:
    def shipWithinDays(self, weights: List[int], D: int) -> int:
        left = max(weights)
        right = sum(weights)
        while left < right:
            mid = (left + right) // 2
            days = 1
            shipped = 0
            for w in weights:
                # if cannot take it, take it tomorrow
                if shipped + w > mid:
                    days += 1
                    if days > D:
                        break
                    shipped = 0
                shipped += w
            if days > D:
                left = mid + 1
            else:
                right = mid
        return left
```
