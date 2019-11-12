## 1239. Maximum Length of a Concatenated String with Unique Characters - 串联字符串的最大长度

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个字符串数组 <code>arr</code>，字符串 <code>s</code> 是将 <code>arr</code> 某一子序列字符串连接所得的字符串，如果 <code>s</code> 中的每一个字符都只出现过一次，那么它就是一个可行解。</p>

<p>请返回所有可行解 <code>s</code> 中最长长度。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>arr = [&quot;un&quot;,&quot;iq&quot;,&quot;ue&quot;]
<strong>输出：</strong>4
<strong>解释：</strong>所有可能的串联组合是 &quot;&quot;,&quot;un&quot;,&quot;iq&quot;,&quot;ue&quot;,&quot;uniq&quot; 和 &quot;ique&quot;，最大长度为 4。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>arr = [&quot;cha&quot;,&quot;r&quot;,&quot;act&quot;,&quot;ers&quot;]
<strong>输出：</strong>6
<strong>解释：</strong>可能的解答有 &quot;chaers&quot; 和 &quot;acters&quot;。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>arr = [&quot;abcdefghijklmnopqrstuvwxyz&quot;]
<strong>输出：</strong>26
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 16</code></li>
	<li><code>1 &lt;= arr[i].length &lt;= 26</code></li>
	<li><code>arr[i]</code>&nbsp;中只含有小写英文字母</li>
</ul>



-----

题目标签：Bit Manipulation / Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 440  ms | 8.8 MB |

```cpp
class Solution {
public:
    void dfs(vector<int>& nums, vector<int>& lens, int n, int cur, int st, int r, int& ret) {
        if (st >= n) {
            return;
        }
        for (int i = st; i < n; i++) {
            if (cur & nums[i]) {
                continue;
            }
            // 不使用该字符串
            dfs(nums, lens, n, cur, i + 1, r, ret);
            cur |= nums[i];
            r += lens[i];
            ret = max(ret, r);
            // 使用该字符串
            dfs(nums, lens, n, cur, i + 1, r, ret);
        }
    }

    int maxLength(vector<string>& arr) {
        vector<int> nums;
        vector<int> lens;
        for (string& s : arr) {
            int t = 0, l = 0;
            bool ok = true;
            for (char c : s) {
                if (t & (1 << (c - 'a'))) {
                    ok = false;
                    break;
                }
                t |= (1 << (c - 'a'));
                l++;
            }
            if (ok) {
                nums.push_back(t);
                lens.push_back(l);
            }
        }
        
        int res = 0;
        dfs(nums, lens, nums.size(), 0, 0, 0, res);
        return res;
    }
};
```
