## 146. LRU Cache - LRU缓存机制

<!--If you want to use the English description, use `question.content` instead-->

<p>运用你所掌握的数据结构，设计和实现一个&nbsp; <a href="https://baike.baidu.com/item/LRU" target="_blank">LRU (最近最少使用) 缓存机制</a>。它应该支持以下操作： 获取数据 <code>get</code> 和 写入数据 <code>put</code> 。</p>

<p>获取数据 <code>get(key)</code> - 如果密钥 (key) 存在于缓存中，则获取密钥的值（总是正数），否则返回 -1。<br>
写入数据 <code>put(key, value)</code> - 如果密钥不存在，则写入其数据值。当缓存容量达到上限时，它应该在写入新数据之前删除最近最少使用的数据值，从而为新的数据值留出空间。</p>

<p><strong>进阶:</strong></p>

<p>你是否可以在&nbsp;<strong>O(1)</strong> 时间复杂度内完成这两种操作？</p>

<p><strong>示例:</strong></p>

<pre>LRUCache cache = new LRUCache( 2 /* 缓存容量 */ );

cache.put(1, 1);
cache.put(2, 2);
cache.get(1);       // 返回  1
cache.put(3, 3);    // 该操作会使得密钥 2 作废
cache.get(2);       // 返回 -1 (未找到)
cache.put(4, 4);    // 该操作会使得密钥 1 作废
cache.get(1);       // 返回 -1 (未找到)
cache.get(3);       // 返回  3
cache.get(4);       // 返回  4
</pre>



-----

题目标签：Design

题目链接：[LeetCode](https://leetcode.com/problems/lru-cache/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/lru-cache/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 64  ms | 59.1 MB |

```java
class LRUCache {

    private static class LinkedNode {
        int key;
        int value;
        LinkedNode pre;
        LinkedNode next;
    }

    private int capacity;
    private HashMap<Integer, LinkedNode> data = new HashMap<>();
    private LinkedNode head = new LinkedNode();
    private LinkedNode tail = new LinkedNode();

    public LRUCache(int capacity) {
        this.capacity = capacity;
        head.next = tail;
        tail.pre = head;
    }

    private void access(int key) {
        LinkedNode node = data.get(key);
        node.pre.next = node.next;
        node.next.pre = node.pre;
        node.next = head.next;
        head.next.pre = node;
        node.pre = head;
        head.next = node;
    }

    public int get(int key) {
        if (data.containsKey(key)) {
            access(key);
            return data.get(key).value;
        } else {
            return -1;
        }
    }

    public void put(int key, int value) {
        if (data.containsKey(key)) {
            access(key);
            head.next.value = value;
        } else {
            if (data.size() >= capacity) {
                data.remove(tail.pre.key);
                tail.pre = tail.pre.pre;
                tail.pre.next = tail;
            }
            LinkedNode node = new LinkedNode();
            node.key = key;
            node.value = value;
            node.next = head.next;
            node.next.pre = node;
            node.pre = head;
            head.next = node;
            data.put(key, node);
        }
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 88  ms | 40.2 MB |

```cpp
class LRUCache {
public:
    list<pair<int, int>> recent;
    unordered_map<int, list<pair<int, int>>::iterator> data;
    int capacity;
    LRUCache(int capacity) {
        this->capacity = capacity;
    }

    int get(int key) {
        if (data.find(key) != data.end()) {
            recent.push_front(*data[key]);
            recent.erase(data[key]);
            data[key] = recent.begin();
            return data[key]->second;
        } else return -1;
    }

    void put(int key, int value) {
        if (data.find(key) != data.end()) {
            recent.erase(data[key]);
        }
        recent.push_front({key, value});
        data[key] = recent.begin();
        if (data.size() > capacity) {
            data.erase(recent.back().first);
            recent.pop_back();
        }
    }
};

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache* obj = new LRUCache(capacity);
 * int param_1 = obj->get(key);
 * obj->put(key,value);
 */
static auto _ = [](){ ios::sync_with_stdio(false); cin.tie(nullptr); return 0; }();
```
