### 461. 汉明距离

> 题目

[链接](https://leetcode-cn.com/problems/hamming-distance/)

> 思路

转为二进制，补0，再对比

> 代码

```js
/**
 * @param {number} x
 * @param {number} y
 * @return {number}
 */
var hammingDistance = function (x, y) {
    x = x.toString(2);
    y = y.toString(2);
    let maxLength = Math.max(x.length, y.length);
    x = x.padStart(maxLength, 0);
    y = y.padStart(maxLength, 0);
    let ans = 0;
    for (let i = 0; i < maxLength; i++) {
        if (x[i] !== y[i]) ans++;
    }
    return ans;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了83.33%的用户

内存消耗：38.1 MB, 在所有 JavaScript 提交中击败了24.13%的用户
