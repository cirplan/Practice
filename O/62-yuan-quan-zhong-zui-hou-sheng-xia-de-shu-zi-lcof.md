### 剑指 Offer 62. 圆圈中最后剩下的数字

> 题目

[链接](https://leetcode-cn.com/problems/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/)

> 思路

??

> 代码

```js
/**
 * @param {number} n
 * @param {number} m
 * @return {number}
 */

var lastRemaining = function (n, m) {
    let x = 0;
    for (let i = 2; i <= n; i++) {
        x = (x + m) % i;
    }
    return x;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了82.27%的用户

内存消耗：38 MB, 在所有 JavaScript 提交中击败了43.37%的用户
