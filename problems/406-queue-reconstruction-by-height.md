## 406. Queue Reconstruction by Height - 根据身高重建队列

<!--If you want to use the English description, use `question.content` instead-->

<p>假设有打乱顺序的一群人站成一个队列。 每个人由一个整数对<code>(h, k)</code>表示，其中<code>h</code>是这个人的身高，<code>k</code>是排在这个人前面且身高大于或等于<code>h</code>的人数。 编写一个算法来重建这个队列。</p>

<p><strong>注意：</strong><br />
总人数少于1100人。</p>

<p><strong>示例</strong></p>

<pre>
输入:
[[7,0], [4,4], [7,1], [5,0], [6,1], [5,2]]

输出:
[[5,0], [7,0], [5,2], [6,1], [4,4], [7,1]]
</pre>



-----

题目标签：Greedy

题目链接：[LeetCode](https://leetcode.com/problems/queue-reconstruction-by-height/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/queue-reconstruction-by-height/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 32  ms | 1.1 MB |

```cpp
class Solution {
public:
    vector<pair<int, int>> reconstructQueue(vector<pair<int, int>>& people) {
        auto cmp = [](pair<int, int>& p1, pair<int, int>& p2) {
            if (p1.first != p2.first) {
                return p1.first > p2.first;
            } else {
                return p1.second < p2.second;
            }
        };
        sort(people.begin(), people.end(), cmp);
        vector<pair<int, int> > res;
        for (auto p : people) {
            res.emplace(res.begin()+p.second, p);
        }
        return res;
    }
};
```
