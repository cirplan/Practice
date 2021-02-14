### 剑指 Offer 31. 栈的压入、弹出序列

> 题目

[链接](https://leetcode-cn.com/problems/zhan-de-ya-ru-dan-chu-xu-lie-lcof/)

> 思路

当入栈的当前元素不等于出栈，则一直查找。如果到最后也没有匹配的，则是不符合的。

> 代码

```js
/**
 * @param {number[]} pushed
 * @param {number[]} popped
 * @return {boolean}
 */
var validateStackSequences = function(pushed, popped) {
    if (!pushed.length) {
        return true;
    }

    let list = [];
    while (popped.length) {
        const num = popped.shift();
        while (pushed.length && list[list.length - 1] !== num) {
            list.push(pushed.shift());
        }
        if (list[list.length - 1] !== num) {
            return false;
        }

        list.pop();
    }

    return true;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了83.38%的用户

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了29.56%的用户