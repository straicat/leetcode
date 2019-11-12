## 134. Gas Station - 加油站

<!--If you want to use the English description, use `question.content` instead-->

<p>在一条环路上有&nbsp;<em>N</em>&nbsp;个加油站，其中第&nbsp;<em>i</em>&nbsp;个加油站有汽油&nbsp;<code>gas[i]</code><em>&nbsp;</em>升。</p>

<p>你有一辆油箱容量无限的的汽车，从第<em> i </em>个加油站开往第<em> i+1&nbsp;</em>个加油站需要消耗汽油&nbsp;<code>cost[i]</code><em>&nbsp;</em>升。你从其中的一个加油站出发，开始时油箱为空。</p>

<p>如果你可以绕环路行驶一周，则返回出发时加油站的编号，否则返回 -1。</p>

<p><strong>说明:</strong>&nbsp;</p>

<ul>
	<li>如果题目有解，该答案即为唯一答案。</li>
	<li>输入数组均为非空数组，且长度相同。</li>
	<li>输入数组中的元素均为非负数。</li>
</ul>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> 
gas  = [1,2,3,4,5]
cost = [3,4,5,1,2]

<strong>输出:</strong> 3

<strong>解释:
</strong>从 3 号加油站(索引为 3 处)出发，可获得 4 升汽油。此时油箱有 = 0 + 4 = 4 升汽油
开往 4 号加油站，此时油箱有 4 - 1 + 5 = 8 升汽油
开往 0 号加油站，此时油箱有 8 - 2 + 1 = 7 升汽油
开往 1 号加油站，此时油箱有 7 - 3 + 2 = 6 升汽油
开往 2 号加油站，此时油箱有 6 - 4 + 3 = 5 升汽油
开往 3 号加油站，你需要消耗 5 升汽油，正好足够你返回到 3 号加油站。
因此，3 可为起始索引。</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 
gas  = [2,3,4]
cost = [3,4,3]

<strong>输出:</strong> -1

<strong>解释:
</strong>你不能从 0 号或 1 号加油站出发，因为没有足够的汽油可以让你行驶到下一个加油站。
我们从 2 号加油站出发，可以获得 4 升汽油。 此时油箱有 = 0 + 4 = 4 升汽油
开往 0 号加油站，此时油箱有 4 - 3 + 2 = 3 升汽油
开往 1 号加油站，此时油箱有 3 - 3 + 3 = 3 升汽油
你无法返回 2 号加油站，因为返程需要消耗 4 升汽油，但是你的油箱只有 3 升汽油。
因此，无论怎样，你都不可能绕环路行驶一周。</pre>



-----

题目标签：Greedy

题目链接：[LeetCode](https://leetcode.com/problems/gas-station/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/gas-station/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1.4 MB |

```cpp
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        int size = gas.size();
        if (size == 0) return -1;
        vector<int> tmp;
        for (int i=0; i<size; ++i) {
            tmp.push_back(gas[i] - cost[i]);
        }
        vector<int> diff;
        diff.insert(diff.end(), tmp.begin(), tmp.end());
        diff.insert(diff.end(), tmp.begin(), tmp.end());
        int i = 0;
        while (i < (int)tmp.size()) {
            while (i < (int)tmp.size() && diff[i] < 0) {  // note: i < tmp.size in while loop
                i++;
            }
            int acc = 0;
            for (int j=i; j<(int)diff.size(); ++j) {
                acc += diff[j];
                if (acc < 0) {
                    i = j + 1;
                    break;
                }
            }
            if (acc >= 0) {
                return i;
            }
        }
        return -1;
    }
};
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
