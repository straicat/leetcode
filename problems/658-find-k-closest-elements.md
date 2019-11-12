## 658. Find K Closest Elements - 找到 K 个最接近的元素

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个排序好的数组，两个整数 <code>k</code> 和 <code>x</code>，从数组中找到最靠近 <code>x</code>（两数之差最小）的 <code>k</code> 个数。返回的结果必须要是按升序排好的。如果有两个数与 <code>x</code> 的差值一样，优先选择数值较小的那个数。</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>
<strong>输入:</strong> [1,2,3,4,5], k=4, x=3
<strong>输出:</strong> [1,2,3,4]
</pre>

<p>&nbsp;</p>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> [1,2,3,4,5], k=4, x=-1
<strong>输出:</strong> [1,2,3,4]
</pre>

<p>&nbsp;</p>

<p><strong>说明:</strong></p>

<ol>
	<li>k 的值为正数，且总是小于给定排序数组的长度。</li>
	<li>数组不为空，且长度不超过 10<sup>4</sup></li>
	<li>数组里的每个元素与&nbsp;x 的绝对值不超过 10<sup>4</sup></li>
</ol>

<p>&nbsp;</p>

<p><strong>更新(2017/9/19):</strong><br />
这个参数 <em>arr</em> 已经被改变为一个<strong>整数数组</strong>（而不是整数列表）。<strong><em>&nbsp;请重新加载代码定义以获取最新更改。</em></strong></p>



-----

题目标签：Binary Search

题目链接：[LeetCode](https://leetcode.com/problems/find-k-closest-elements/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-k-closest-elements/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 23  ms | 41.2 MB |

```java
class Solution {
    class Node {
        int value;
        int interval;
        Node(int value, int interval) {
            this.value = value;
            this.interval = interval;
        }
    }

    public List<Integer> findClosestElements(int[] arr, int k, int x) {
        Node[] nds = new Node[arr.length];
        for (int i = 0; i < arr.length; i++) {
            nds[i] = new Node(arr[i], Math.abs(arr[i] - x));
        }
        Arrays.sort(nds, new Comparator<Node>() {
            @Override
            public int compare(Node o1, Node o2) {
                return o1.interval == o2.interval ? o1.value - o2.value : o1.interval - o2.interval;
            }
        });
        List<Integer> res = new ArrayList<>();
        for (int i = 0; i < k; i++) {
            res.add(nds[i].value);
        }
        res.sort(null);
        return res;
    }
}
```
