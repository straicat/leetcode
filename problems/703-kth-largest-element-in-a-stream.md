## 703. Kth Largest Element in a Stream - 数据流中的第K大元素

<!--If you want to use the English description, use `question.content` instead-->

<p>设计一个找到数据流中第K大元素的类（class）。注意是排序后的第K大元素，不是第K个不同的元素。</p>

<p>你的&nbsp;<code>KthLargest</code>&nbsp;类需要一个同时接收整数&nbsp;<code>k</code> 和整数数组<code>nums</code>&nbsp;的构造器，它包含数据流中的初始元素。每次调用&nbsp;<code>KthLargest.add</code>，返回当前数据流中第K大的元素。</p>

<p><strong>示例:</strong></p>

<pre>
int k = 3;
int[] arr = [4,5,8,2];
KthLargest kthLargest = new KthLargest(3, arr);
kthLargest.add(3);&nbsp; &nbsp;// returns 4
kthLargest.add(5);&nbsp; &nbsp;// returns 5
kthLargest.add(10);&nbsp; // returns 5
kthLargest.add(9);&nbsp; &nbsp;// returns 8
kthLargest.add(4);&nbsp; &nbsp;// returns 8
</pre>

<p><strong>说明: </strong><br />
你可以假设&nbsp;<code>nums</code>&nbsp;的长度&ge;&nbsp;<code>k-1</code>&nbsp;且<code>k</code> &ge;&nbsp;1。</p>



-----

题目标签：Heap

题目链接：[LeetCode](https://leetcode.com/problems/kth-largest-element-in-a-stream/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/kth-largest-element-in-a-stream/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 52  ms | 19.2 MB |

```cpp
class KthLargest {
public:
    int size;
    // 小根堆
    priority_queue<int, vector<int>, greater<int>> pq;
    KthLargest(int k, vector<int>& nums) {
        size = k;
        for (int n : nums)
            add(n);
    }

    int add(int val) {
        pq.push(val);
        while (pq.size() > size) {
            pq.pop();
        }
        return pq.top();
    }
};

/**
 * Your KthLargest object will be instantiated and called as such:
 * KthLargest* obj = new KthLargest(k, nums);
 * int param_1 = obj->add(val);
 */
```
