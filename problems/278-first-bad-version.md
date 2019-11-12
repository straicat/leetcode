## 278. First Bad Version - 第一个错误的版本

<!--If you want to use the English description, use `question.content` instead-->

<p>你是产品经理，目前正在带领一个团队开发新的产品。不幸的是，你的产品的最新版本没有通过质量检测。由于每个版本都是基于之前的版本开发的，所以错误的版本之后的所有版本都是错的。</p>

<p>假设你有 <code>n</code> 个版本 <code>[1, 2, ..., n]</code>，你想找出导致之后所有版本出错的第一个错误的版本。</p>

<p>你可以通过调用&nbsp;<code>bool isBadVersion(version)</code>&nbsp;接口来判断版本号 <code>version</code> 是否在单元测试中出错。实现一个函数来查找第一个错误的版本。你应该尽量减少对调用 API 的次数。</p>

<p><strong>示例:</strong></p>

<pre>给定 n = 5，并且 version = 4 是第一个错误的版本。

<code>调用 isBadVersion(3) -&gt; false
调用 isBadVersion(5)&nbsp;-&gt; true
调用 isBadVersion(4)&nbsp;-&gt; true

所以，4 是第一个错误的版本。&nbsp;</code></pre>



-----

题目标签：Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/first-bad-version/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/first-bad-version/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | 827.4 KB |

```cpp
// Forward declaration of isBadVersion API.
bool isBadVersion(int version);

class Solution {
public:
    int firstBadVersion(int n) {
        int low = 1, high = n;
        int mid = 1;
        while (low <= high) {
            mid = low + (high - low) / 2;
            if (isBadVersion(mid)) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return mid + (!isBadVersion(mid));
    }
};
```
