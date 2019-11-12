## 284. Peeking Iterator - 顶端迭代器

<!--If you want to use the English description, use `question.content` instead-->

<p>给定一个迭代器类的接口，接口包含两个方法：&nbsp;<code>next()</code>&nbsp;和&nbsp;<code>hasNext()</code>。设计并实现一个支持&nbsp;<code>peek()</code>&nbsp;操作的顶端迭代器 -- 其本质就是把原本应由&nbsp;<code>next()</code>&nbsp;方法返回的元素&nbsp;<code>peek()</code>&nbsp;出来。</p>

<p><strong>示例:</strong></p>

<pre>假设迭代器被初始化为列表&nbsp;<strong><code>[1,2,3]</code></strong>。

调用&nbsp;<strong><code>next() </code></strong>返回 <strong>1</strong>，得到列表中的第一个元素。
现在调用&nbsp;<strong><code>peek()</code></strong>&nbsp;返回 <strong>2</strong>，下一个元素。在此之后调用&nbsp;<strong><code>next() </code></strong>仍然返回 <strong>2</strong>。
最后一次调用&nbsp;<strong><code>next()</code></strong>&nbsp;返回 <strong>3</strong>，末尾元素。在此之后调用&nbsp;<strong><code>hasNext()</code></strong>&nbsp;应该返回 <strong>false</strong>。
</pre>

<p><strong>进阶：</strong>你将如何拓展你的设计？使之变得通用化，从而适应所有的类型，而不只是整数型？</p>



-----

题目标签：Design

题目链接：[LeetCode](https://leetcode.com/problems/peeking-iterator/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/peeking-iterator/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 1 MB |

```cpp
// Below is the interface for Iterator, which is already defined for you.
// **DO NOT** modify the interface for Iterator.
class Iterator {
    struct Data;
    Data* data;
public:
    Iterator(const vector<int>& nums);
    Iterator(const Iterator& iter);
    virtual ~Iterator();
    // Returns the next element in the iteration.
    int next();
    // Returns true if the iteration has more elements.
    bool hasNext() const;
};


class PeekingIterator : public Iterator {
public:
    int pos = 0;
    vector<int> vec;
    PeekingIterator(const vector<int>& nums) : Iterator(nums) {
        // Initialize any member here.
        // **DO NOT** save a copy of nums and manipulate it directly.
        // You should only use the Iterator interface methods.
        vec = nums;
    }

    // Returns the next element in the iteration without advancing the iterator.
    int peek() {
        return vec[pos];
    }

    // hasNext() and next() should behave the same as in the Iterator interface.
    // Override them if needed.
    int next() {
        int t = peek();
        pos++;
        return t;
    }

    bool hasNext() const {
        return pos < vec.size();
    }
};
```
