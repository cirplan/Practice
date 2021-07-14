### 191. 位1的个数

> 题目

[链接](https://leetcode-cn.com/problems/number-of-1-bits/)

> 思路

？

> 代码

```js
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function (n) {
    let ret = 0;
    for (let i = 0; i < 32; i++) {
        if ((n & (1 << i)) !== 0) {
            ret++;
        }
    }
    return ret;
};
```

> 复杂度分析

时间复杂度：O(K)。K 是二进制位数

空间复杂度：O(1)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了58.68%的用户

内存消耗：39 MB, 在所有 JavaScript 提交中击败了92.14%的用户
