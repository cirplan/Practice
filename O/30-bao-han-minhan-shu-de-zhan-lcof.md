### 剑指 Offer 30. 包含min函数的栈

> 题目

[链接](https://leetcode-cn.com/problems/bao-han-minhan-shu-de-zhan-lcof/)

> 思路

使用辅助最小栈

> 代码

```js
/**
 * initialize your data structure here.
 */
var MinStack = function() {
    this.stack = [];
    this.minStack = [];
};

/** 
 * @param {number} x
 * @return {void}
 */
MinStack.prototype.push = function(x) {
    if (!this.stack.length) {
        this.minStack.push(x);
    } else {
        this.minStack.push(Math.min(this.min(), x));
    }
    this.stack.push(x);
};

/**
 * @return {void}
 */
MinStack.prototype.pop = function() {
    this.minStack.pop();
    this.stack.pop();
};

/**
 * @return {number}
 */
MinStack.prototype.top = function() {
    return this.stack[this.stack.length - 1];
};

/**
 * @return {number}
 */
MinStack.prototype.min = function() {
    return this.minStack[this.minStack.length - 1];
};

/**
 * Your MinStack object will be instantiated and called as such:
 * var obj = new MinStack()
 * obj.push(x)
 * obj.pop()
 * var param_3 = obj.top()
 * var param_4 = obj.min()
 */
```

> 复杂度分析

时间复杂度：O(1)。

空间复杂度：O(N)。

> 执行

执行用时：136 ms, 在所有 JavaScript 提交中击败了55.71%的用户

内存消耗：45.1 MB, 在所有 JavaScript 提交中击败了23.79%的用户