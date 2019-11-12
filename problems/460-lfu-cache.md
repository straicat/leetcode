## 460. LFU Cache - LFU缓存

<!--If you want to use the English description, use `question.content` instead-->

<p>设计并实现<a href="https://baike.baidu.com/item/%E7%BC%93%E5%AD%98%E7%AE%97%E6%B3%95">最不经常使用（LFU）</a>缓存的数据结构。它应该支持以下操作：<code>get</code>&nbsp;和&nbsp;<code>put</code>。</p>

<p><code>get(key)</code>&nbsp;- 如果键存在于缓存中，则获取键的值（总是正数），否则返回 -1。<br />
<code>put(key, value)</code>&nbsp;- 如果键不存在，请设置或插入值。当缓存达到其容量时，它应该在插入新项目之前，使最不经常使用的项目无效。在此问题中，当存在平局（即两个或更多个键具有相同使用频率）时，<strong>最近</strong>最少使用的键将被去除。</p>

<p><strong>进阶：</strong><br />
你是否可以在&nbsp;<strong>O(1)&nbsp;</strong>时间复杂度内执行两项操作？</p>

<p><strong>示例：</strong></p>

<pre>
LFUCache cache = new LFUCache( 2 /* capacity (缓存容量) */ );

cache.put(1, 1);
cache.put(2, 2);
cache.get(1);       // 返回 1
cache.put(3, 3);    // 去除 key 2
cache.get(2);       // 返回 -1 (未找到key 2)
cache.get(3);       // 返回 3
cache.put(4, 4);    // 去除 key 1
cache.get(1);       // 返回 -1 (未找到 key 1)
cache.get(3);       // 返回 3
cache.get(4);       // 返回 4</pre>



-----

题目标签：Design

题目链接：[LeetCode](https://leetcode.com/problems/lfu-cache/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/lfu-cache/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 81  ms | 60.8 MB |

```java
class LFUCache {

    HashMap<Integer, Integer> data = new HashMap<>();
    HashMap<Integer, Integer> cnt = new HashMap<>();
    HashMap<Integer, LinkedHashSet<Integer>> freq = new HashMap<>();
    int capacity;
    int min = 0;

    public LFUCache(int capacity) {
        this.capacity = capacity;
    }

    public int get(int key) {
        if (!data.containsKey(key))
            return -1;
        int value = data.get(key);
        int count = cnt.get(key);
        cnt.put(key, count + 1);
        freq.get(count).remove(key);
        if (!freq.containsKey(count + 1))
            freq.put(count + 1, new LinkedHashSet<>());
        freq.get(count + 1).add(key);
        if (freq.get(count).size() == 0 && count == min)
            min++;
        return value;
    }

    public void put(int key, int value) {
        if (capacity <= 0) return;
        if (data.containsKey(key)) {
            data.put(key, value);
            get(key);
        } else {
            if (data.size() >= capacity) {
                int del = freq.get(min).iterator().next();
                data.remove(del);
                cnt.remove(del);
                freq.get(min).remove(del);
            }
            data.put(key, value);
            cnt.put(key, 1);
            if (!freq.containsKey(1))
                freq.put(1, new LinkedHashSet<>());
            freq.get(1).add(key);
            min = 1;
        }
    }
}

/**
 * Your LFUCache object will be instantiated and called as such:
 * LFUCache obj = new LFUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```
