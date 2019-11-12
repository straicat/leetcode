## 225. Implement Stack using Queues - 用队列实现栈

<!--If you want to use the English description, use `question.content` instead-->

<p>使用队列实现栈的下列操作：</p>

<ul>
	<li>push(x) -- 元素 x 入栈</li>
	<li>pop() -- 移除栈顶元素</li>
	<li>top() -- 获取栈顶元素</li>
	<li>empty() -- 返回栈是否为空</li>
</ul>

<p><strong>注意:</strong></p>

<ul>
	<li>你只能使用队列的基本操作-- 也就是&nbsp;<code>push to back</code>, <code>peek/pop from front</code>, <code>size</code>, 和&nbsp;<code>is empty</code>&nbsp;这些操作是合法的。</li>
	<li>你所使用的语言也许不支持队列。&nbsp;你可以使用 list 或者 deque（双端队列）来模拟一个队列&nbsp;, 只要是标准的队列操作即可。</li>
	<li>你可以假设所有操作都是有效的（例如, 对一个空的栈不会调用 pop 或者 top 操作）。</li>
</ul>



-----

题目标签：Stack / Design

题目链接：[LeetCode](https://leetcode.com/problems/implement-stack-using-queues/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/implement-stack-using-queues/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | 901.1 KB |

```cpp
class MyStack {
public:
    queue<int> a;
    /** Initialize your data structure here. */
    MyStack() {
        
    }
    
    /** Push element x onto stack. */
    void push(int x) {
        a.push(x);
        for (int i=0; i<a.size()-1; ++i) {
            int t = a.front();
            a.pop();
            a.push(t);
        }
    }
    
    /** Removes the element on top of the stack and returns that element. */
    int pop() {
        int t = a.front();
        a.pop();
        return t;
    }
    
    /** Get the top element. */
    int top() {
        return a.front();
    }
    
    /** Returns whether the stack is empty. */
    bool empty() {
        return a.empty();
    }
};

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack obj = new MyStack();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.top();
 * bool param_4 = obj.empty();
 */
```
