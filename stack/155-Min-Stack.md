### 155. 最小栈

> 题目

设计一个支持 push ，pop ，top 操作，并能在常数时间内检索到最小元素的栈。

push(x) —— 将元素 x 推入栈中。
pop() —— 删除栈顶的元素。
top() —— 获取栈顶元素。
getMin() —— 检索栈中的最小元素。

示例:
```js
输入：
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

输出：
[null,null,null,null,-3,null,0,-2]

解释：
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.getMin();   --> 返回 -2.
```

提示：
pop、top 和 getMin 操作总是在 非空栈 上调用。

> 思路

关键是常数时间内检索到最小元素。因为栈的结构，我们使用辅助最小栈。

> 代码

```js
/**
 * initialize your data structure here.
 */
var MinStack = function () {
    this.list = [];
    this.minList = [];
};

/** 
 * @param {number} x
 * @return {void}
 */
MinStack.prototype.push = function (x) {
    if (this.minList.length) {
        this.minList.push(Math.min(this.minList[this.minList.length - 1], x));
    } else {
        this.minList.push(x);
    }
    this.list.push(x);
};

/**
 * @return {void}
 */
MinStack.prototype.pop = function () {
    this.minList.pop();
    this.list.pop();
};

/**
 * @return {number}
 */
MinStack.prototype.top = function () {
    return this.list[this.list.length - 1];
};

/**
 * @return {number}
 */
MinStack.prototype.getMin = function () {
    return this.minList[this.minList.length - 1]
};

/**
 * Your MinStack object will be instantiated and called as such:
 * var obj = new MinStack()
 * obj.push(x)
 * obj.pop()
 * var param_3 = obj.top()
 * var param_4 = obj.getMin()
 */
```

> 复杂度分析

时间复杂度 : O(1)。

空间复杂度 : O(N)。

> 执行

执行用时：132 ms, 在所有 JavaScript 提交中击败了86.69%的用户。

内存消耗：44.5 MB, 在所有 JavaScript 提交中击败了36.25%的用户。

> 算法

