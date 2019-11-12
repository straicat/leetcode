## 155. Min Stack - 最小栈

<!--If you want to use the English description, use `question.content` instead-->

<p>设计一个支持 push，pop，top 操作，并能在常数时间内检索到最小元素的栈。</p>

<ul>
	<li>push(x)&nbsp;-- 将元素 x 推入栈中。</li>
	<li>pop()&nbsp;-- 删除栈顶的元素。</li>
	<li>top()&nbsp;-- 获取栈顶元素。</li>
	<li>getMin() -- 检索栈中的最小元素。</li>
</ul>

<p><strong>示例:</strong></p>

<pre>MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --&gt; 返回 -3.
minStack.pop();
minStack.top();      --&gt; 返回 0.
minStack.getMin();   --&gt; 返回 -2.
</pre>



-----

题目标签：Stack / Design

题目链接：[LeetCode](https://leetcode.com/problems/min-stack/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/min-stack/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 60  ms | 17.2 MB |

```python3
'''
push -2: [INF, -2],               min: -2
push 0 : [INF, -2, 0],            min: -2
push -3: [INF, -2, 0, -2, -3],    min: -3
'''

class MinStack:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.data = []
        self.min = 1e20

    def push(self, x: int) -> None:
        # 当值不大于当前最小值时，先压人原最小值，再将最小值更新为当前值；最后压人当前值
        if (x <= self.min):
            self.data.append(self.min)
            self.min = x
        self.data.append(x)

    def pop(self) -> None:
        # 如果顶部元素等于最小值，将其弹出，并再弹一个元素且将此元素更新为最小值；否则仅弹出
        if self.top() == self.min:
            self.data.pop()
            self.min = self.data.pop()
        else:
            self.data.pop()

    def top(self) -> int:
        return self.data[-1]

    def getMin(self) -> int:
        return self.min


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(x)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 49  ms | 41.3 MB |

```java
class MinStack {

    /** initialize your data structure here. */
    private Stack<Integer> data;
    private PriorityQueue<Integer> mins;
    public MinStack() {
        data = new Stack<>();
        mins = new PriorityQueue<>();
    }

    public void push(int x) {
        data.push(x);
        mins.add(x);
    }

    public void pop() {
        mins.remove(data.pop());
    }

    public int top() {
        return data.peek();
    }

    public int getMin() {
        return mins.peek();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
```
