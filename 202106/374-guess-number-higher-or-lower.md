### 374. 猜数字大小

> 题目

[链接](https://leetcode-cn.com/problems/guess-number-higher-or-lower/)

> 思路

二分

> 代码

```js
/** 
 * Forward declaration of guess API.
 * @param {number} num   your guess
 * @return 	            -1 if num is lower than the guess number
 *			             1 if num is higher than the guess number
 *                       otherwise return 0
 * var guess = function(num) {}
 */

/**
 * @param {number} n
 * @return {number}
 */
var guessNumber = function(n) {
    let left = 1;
    let right = n;
    while (left < right) {
        const mid = left + parseInt((right - left) / 2);
        const res = guess(mid);
        if (res === 0) {
            return mid;
        } else if (res > 0) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return left;
};
```

> 复杂度分析

时间复杂度：O(logn)。

空间复杂度：O(1)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了21.48%的用户

内存消耗：38 MB, 在所有 JavaScript 提交中击败了9.35%的用户
