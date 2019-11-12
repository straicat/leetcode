## 17. Letter Combinations of a Phone Number - 电话号码的字母组合

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个仅包含数字&nbsp;<code>2-9</code>&nbsp;的字符串，返回所有它能表示的字母组合。</p>

<p>给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/original_images/17_telephone_keypad.png" style="width: 200px;"></p>

<p><strong>示例:</strong></p>

<pre><strong>输入：</strong>&quot;23&quot;
<strong>输出：</strong>[&quot;ad&quot;, &quot;ae&quot;, &quot;af&quot;, &quot;bd&quot;, &quot;be&quot;, &quot;bf&quot;, &quot;cd&quot;, &quot;ce&quot;, &quot;cf&quot;].
</pre>

<p><strong>说明:</strong><br>
尽管上面的答案是按字典序排列的，但是你可以任意选择答案输出的顺序。</p>



-----

题目标签：String / Backtracking

题目链接：[LeetCode](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/description/)

## 题解

这个就是排列组合，可以使用递归。注意7和9上面有4个字母。

| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 0  ms | N/A |

```cpp
class Solution {
public:
    map<string, string> dia = {
        {"2", "abc"},
        {"3", "def"},
        {"4", "ghi"},
        {"5", "jkl"},
        {"6", "mno"},
        {"7", "pqrs"},
        {"8", "tuv"},
        {"9", "wxyz"}
    };
    vector<string> letterCombinations(string digits) {
        vector<string> res;
        if(!digits.length()){
            return res;
        }
        if(digits.length() == 1){
            if(dia.count(digits)){
                for(int i=0; i<(int)dia.at(digits).length(); ++i){
                    res.push_back(dia.at(digits).substr(i, 1));
                }
            }
            return res;
        }
        vector<string> res1 = letterCombinations(digits.substr(0, 1));
        vector<string> res2 = letterCombinations(digits.substr(1, digits.length()-1));
        for(string s1 : res1){
            for(string s2 : res2){
                res.push_back(s1 + s2);
            }
        }
        return res;
    }
};
```
