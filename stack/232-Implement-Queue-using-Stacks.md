### 232. 用栈实现队列

> 题目

请你仅使用两个栈实现先入先出队列。队列应当支持一般队列的支持的所有操作（push、pop、peek、empty）：

实现 MyQueue 类：

void push(int x) 将元素 x 推到队列的末尾
int pop() 从队列的开头移除并返回元素
int peek() 返回队列开头的元素
boolean empty() 如果队列为空，返回 true ；否则，返回 false
 
说明：

你只能使用标准的栈操作 —— 也就是只有 push to top, peek/pop from top, size, 和 is empty 操作是合法的。
你所使用的语言也许不支持栈。你可以使用 list 或者 deque（双端队列）来模拟一个栈，只要是标准的栈操作即可。

进阶：

你能否实现每个操作均摊时间复杂度为 O(1) 的队列？换句话说，执行 n 个操作的总时间复杂度为 O(n) ，即使其中一个操作可能花费较长时间。
 
示例：
```
输入：
["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]
输出：
[null, null, null, 1, 1, false]

解释：
MyQueue myQueue = new MyQueue();
myQueue.push(1); // queue is: [1]
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
myQueue.peek(); // return 1
myQueue.pop(); // return 1, queue is [2]
myQueue.empty(); // return false 
```

提示：

1 <= x <= 9
最多调用 100 次 push、pop、peek 和 empty
假设所有操作都是有效的 （例如，一个空的队列不会调用 pop 或者 peek 操作）

> 思路

关键是 pop 和 peek 怎么取。用两个栈，可以使用搬运的方式，先把栈的元素般到另一个栈，找到栈顶元素，再把另一个栈的元素搬回来。

> 代码

```js
/**
 * Initialize your data structure here.
 */
var MyQueue = function () {
    this.stack_list = [];
    this.first = null;
};

/**
 * Push element x to the back of queue.
 * @param {number} x
 * @return {void}
 */
MyQueue.prototype.push = function (x) {
    if (!this.stack_list.length) {
        this.first = x;
    }
    this.stack_list.push(x);
};

/**
 * Removes the element from in front of queue and returns that element.
 * @return {number}
 */
MyQueue.prototype.pop = function () {
    let { stack_list } = this;
    let second_stack_list = [];
    let first;
    while (stack_list.length) {
        let node = stack_list.pop();
        if (stack_list.length === 0) {
            first = node;
        } else {
            second_stack_list.push(node);
        }
    }

    while (second_stack_list.length) {
        let val = second_stack_list.pop();
        if (!stack_list.length) {
            this.first = val;
        }
        stack_list.push(val);
    }

    return first;
};

/**
 * Get the front element.
 * @return {number}
 */
MyQueue.prototype.peek = function () {
    return this.first;
};

/**
 * Returns whether the queue is empty.
 * @return {boolean}
 */
MyQueue.prototype.empty = function () {
    return this.stack_list.length === 0;
};

/**
 * Your MyQueue object will be instantiated and called as such:
 * var obj = new MyQueue()
 * obj.push(x)
 * var param_2 = obj.pop()
 * var param_3 = obj.peek()
 * var param_4 = obj.empty()
 */
```

> 复杂度分析

push：时间复杂度 : O(1)；空间复杂度 : O(1)。

pop : O(N)；空间复杂度 : O(N)。

peek : O(1)；空间复杂度 : O(1)。

empty : O(1)；空间复杂度 : O(1)。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了91.59%的用户。

内存消耗：37.6 MB, 在所有 JavaScript 提交中击败了5.05%的用户。

> 算法

