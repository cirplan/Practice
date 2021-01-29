### 剑指 Offer 09. 用两个栈实现队列

> 题目

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，
分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )

示例 1：

```
输入：
["CQueue","appendTail","deleteHead","deleteHead"]
[[],[3],[],[]]
输出：[null,null,3,-1]
```

示例 2：

```
输入：
["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
[[],[],[5],[2],[],[]]
输出：[null,-1,null,null,5,2]
```

提示：

1 <= values <= 10000
最多会对 appendTail、deleteHead 进行 10000 次调用

> 思路

用两个栈，一个维护新增数据，一个维护删除数据。栈2中没数据，则把栈1都推过去。新增则新增到栈1。

> 代码

```js
var CQueue = function () {
    this.stack1 = [];
    this.stack2 = [];
};

/** 
 * @param {number} value
 * @return {void}
 */
CQueue.prototype.appendTail = function (value) {
    this.stack1.push(value);
};

/**
 * @return {number}
 */
CQueue.prototype.deleteHead = function () {
    const { stack1, stack2 } = this;
    const len1 = stack1.length;
    const len2 = stack2.length;
    if (!len1 && !len2) {
        return -1;
    } else if (len2) {
        return stack2.pop();
    } else {
        while (stack1.length) {
            stack2.push(stack1.pop());
        }

        return stack2.pop();;
    }
};

/**
 * Your CQueue object will be instantiated and called as such:
 * var obj = new CQueue()
 * obj.appendTail(value)
 * var param_2 = obj.deleteHead()
 */
```

> 复杂度分析

时间复杂度 : appendTail 为O(1)，deleteHead 为O(n)。

空间复杂度 : O(n)。

> 执行

执行用时：396 ms, 在所有 JavaScript 提交中击败了76.81%的用户

内存消耗：49.8 MB, 在所有 JavaScript 提交中击败了22.81%的用户