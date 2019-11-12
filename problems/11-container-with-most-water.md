## 11. Container With Most Water - 盛最多水的容器

<!--If you want to use the English description, use `question.content` instead-->

<p>给定 <em>n</em> 个非负整数 <em>a</em><sub>1</sub>，<em>a</em><sub>2，</sub>...，<em>a</em><sub>n，</sub>每个数代表坐标中的一个点&nbsp;(<em>i</em>,&nbsp;<em>a<sub>i</sub></em>) 。在坐标内画 <em>n</em> 条垂直线，垂直线 <em>i</em>&nbsp;的两个端点分别为&nbsp;(<em>i</em>,&nbsp;<em>a<sub>i</sub></em>) 和 (<em>i</em>, 0)。找出其中的两条线，使得它们与&nbsp;<em>x</em>&nbsp;轴共同构成的容器可以容纳最多的水。</p>

<p><strong>说明：</strong>你不能倾斜容器，且&nbsp;<em>n</em>&nbsp;的值至少为 2。</p>

<p><img alt="" src="https://aliyun-lc-upload.oss-cn-hangzhou.aliyuncs.com/aliyun-lc-upload/uploads/2018/07/25/question_11.jpg" style="height: 287px; width: 600px;"></p>

<p><small>图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为&nbsp;49。</small></p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,8,6,2,5,4,8,3,7]
<strong>输出:</strong> 49</pre>



-----

题目标签：Array / Two Pointers

题目链接：[LeetCode](https://leetcode.com/problems/container-with-most-water/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/container-with-most-water/description/)

## 题解

这题的意思就是，从数组里选择两个数，使得两者的间距与较小的那个数的乘积最大。

这题可以用暴力穷举法做，比较简单。不过，假如不暴力枚举，可以怎么做呢？

**双指针夹逼法**。双指针初始位于两端，然后向中间移动，每次移动高度较小的指针，期间更新最大面积。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | N/A |

```cpp
static auto _ = [](){
  std::ios::sync_with_stdio(false);
  std::cin.tie(NULL);
  return 0;
}();

class Solution {
public:
    int maxArea(vector<int>& height) {
        if(height.size() < 2){
            return 0;
        }
        int res = 0;
        int left = 0, right = height.size() - 1;
        while(left < right){
            res = max(res, (right-left) * min(height.at(left), height.at(right)));
            if(height.at(left) < height.at(right)){
                left++;
            }else{
                right--;
            }
        }
        return res;
    }
};
```
