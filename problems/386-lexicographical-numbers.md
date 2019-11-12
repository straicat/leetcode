## 386. Lexicographical Numbers - 字典序排数

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个整数&nbsp;<em>n</em>, 返回从&nbsp;<em>1&nbsp;</em>到&nbsp;<em>n&nbsp;</em>的字典顺序。</p>

<p>例如，</p>

<p>给定 <em>n</em> =1 3，返回 [1,10,11,12,13,2,3,4,5,6,7,8,9] 。</p>

<p>请尽可能的优化算法的时间复杂度和空间复杂度。 输入的数据&nbsp;<em>n&nbsp;</em>小于等于&nbsp;5,000,000。</p>



-----

题目标签：

题目链接：[LeetCode](https://leetcode.com/problems/lexicographical-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/lexicographical-numbers/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 84  ms | 1.9 MB |

```cpp
class Solution {
public:
    void dfs(vector<int>& res, int n, int st) {
        if (st > n) return;
        for (int i = st; i <= n && i / 10 == st / 10; ++i) {
            res.push_back(i);
            dfs(res, n, i * 10);
        }
    }

    vector<int> lexicalOrder(int n) {
        vector<int> res;
        dfs(res, n, 1);
        return res;
    }
};
```
