### 201. 数字范围按位与

> 题目

[链接](https://leetcode-cn.com/problems/bitwise-and-of-numbers-range/)

> 思路

??

> 代码

```js
/**
 * @param {number} left
 * @param {number} right
 * @return {number}
 */
var rangeBitwiseAnd = function (m, n) {
    while (m < n) {
        // 抹去最右边的 1
        n = n & (n - 1);
    }
    return n;
};
```

> 复杂度分析

时间复杂度：O(logn)。

空间复杂度：O(1)。

> 执行

执行用时：168 ms, 在所有 JavaScript 提交中击败了98.02%的用户

内存消耗：44.6 MB, 在所有 JavaScript 提交中击败了95.05%的用户
