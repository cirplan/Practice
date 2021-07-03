### 172. 阶乘后的零

> 题目

[链接](https://leetcode-cn.com/problems/factorial-trailing-zeroes/)

> 思路

寻找5

> 代码

```js
/**
 * @param {number} n
 * @return {number}
 */
var trailingZeroes = function (n) {
    let r = 0;
    while (n > 1) {
        n = parseInt(n / 5);
        r += n;
    }
    return r;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(1)。

> 执行

执行用时：132 ms, 在所有 JavaScript 提交中击败了5.73%的用户

内存消耗：39.1 MB, 在所有 JavaScript 提交中击败了67.87%的用户
