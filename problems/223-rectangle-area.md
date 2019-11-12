## 223. Rectangle Area - 矩形面积

<!--If you want to use the English description, use `question.content` instead-->

<p>在<strong>二维</strong>平面上计算出两个<strong>由直线构成的</strong>矩形重叠后形成的总面积。</p>

<p>每个矩形由其左下顶点和右上顶点坐标表示，如图所示。</p>

<p><img alt="Rectangle Area" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/rectangle_area.png"></p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> -3, 0, 3, 4, 0, -1, 9, 2
<strong>输出:</strong> 45</pre>

<p><strong>说明:</strong> 假设矩形面积不会超出&nbsp;<strong>int&nbsp;</strong>的范围。</p>



-----

题目标签：Math

题目链接：[LeetCode](https://leetcode.com/problems/rectangle-area/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/rectangle-area/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 16  ms | 864.3 KB |

```cpp
class Solution {
public:
    int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
        int area1 = (C - A) * (D - B);
        int area2 = (G - E) * (H - F);
        if (C <= E || D <= F || H <= B || G <= A) {
            return area1 + area2;
        } else {
            int area3 = (min(C, G) - max(A, E)) * (min(D, H) - max(B, F));
            return area1 + area2 - area3;
        }
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
