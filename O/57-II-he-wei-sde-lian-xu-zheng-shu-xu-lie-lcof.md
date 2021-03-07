### 剑指 Offer 57 - II. 和为s的连续正数序列

> 题目

[链接](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

> 思路

使用一个数组，从1开始，当数组的和小于target，则往数组里加i。如果数组的和大于target，则把数组第一项弹出。

> 代码

```js
/**
 * @param {number} target
 * @return {number[][]}
 */
var findContinuousSequence = function(target) {
    let i = 1;
    let result = [];
    let temp = [];
    while (i < target) {
        let sum = temp.reduce((total, num) => (total + num), 0);
        if (sum === target) {
            result.push(temp.slice());
            temp.shift();
        } else if (sum < target) {
            temp.push(i++);
        } else {
            if (temp.length === 2) {
                return result;
            } else {
                temp.shift();
            }
        }
    }
    
    return result;
};
```

> 复杂度分析

时间复杂度：O(target)。

空间复杂度：O(target)。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了34.12%的用户

内存消耗：39.6 MB, 在所有 JavaScript 提交中击败了32.78%的用户