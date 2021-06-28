### 48. 旋转图像

> 题目

[链接](https://leetcode-cn.com/problems/rotate-image/)

> 思路

旋转

> 代码

```js
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var rotate = function (matrix) {
    const n = matrix.length;
    // 水平翻转
    for (let i = 0; i < Math.floor(n / 2); i++) {
        for (let j = 0; j < n; j++) {
            [matrix[i][j], matrix[n - i - 1][j]] = [matrix[n - i - 1][j], matrix[i][j]];
        }
    }
    // 主对角线翻转
    for (let i = 0; i < n; i++) {
        for (let j = 0; j < i; j++) {
            [matrix[i][j], matrix[j][i]] = [matrix[j][i], matrix[i][j]];
        }
    }

};
```

> 复杂度分析

时间复杂度：O(N ^ 2)。

空间复杂度：O(1)。

> 执行
执行用时：72 ms, 在所有 JavaScript 提交中击败了97.69%的用户

内存消耗：40.4 MB, 在所有 JavaScript 提交中击败了9.75%的用户