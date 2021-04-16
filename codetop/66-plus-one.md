### 66. 加一

> 题目

[链接](https://leetcode-cn.com/problems/plus-one/)

> 思路

注意判断9和首位

> 代码

```js
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function (digits) {
    const n = digits.length;
    for (let i = n - 1; i >= 0; i--) {
        if (digits[i] != 9) {
            digits[i]++;
            return digits;
        } else {
            digits[i] = 0;
        }
        if (i == 0) {
            digits.unshift(1);
            return digits;
        }
    }
    retrun - 1;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：72 ms, 在所有 JavaScript 提交中击败了97.28%的用户

内存消耗：38.2 MB, 在所有 JavaScript 提交中击败了8.81%的用户

