### 739. 每日温度

> 题目

[链接](https://leetcode-cn.com/problems/daily-temperatures/)

> 思路

使用单调栈

> 代码

```js
/**
 * @param {number[]} temperatures
 * @return {number[]}
 */
var dailyTemperatures = function (T) {
    const res = new Array(T.length).fill(0)
    const stack = []
    for (let i = T.length - 1; i >= 0; i--) {
        while (stack.length && T[i] >= T[stack[stack.length - 1]]) {
            stack.pop()
        }
        if (stack.length) {
            res[i] = stack[stack.length - 1] - i
        }
        stack.push(i)
    }
    return res
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：180 ms, 在所有 JavaScript 提交中击败了67.40%的用户

内存消耗：47.9 MB, 在所有 JavaScript 提交中击败了66.71%的用户
