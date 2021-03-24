### 面试题 01.07. 旋转矩阵

> 题目

[链接](https://leetcode-cn.com/problems/rotate-matrix-lcci/)

> 思路

先水平翻转，再对角线翻转

> 代码

```js
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var rotate = function (matrix) {
    let n = matrix.length;
    // 水平翻转
    for (let i = 0; i < n / 2; ++i) {
        for (let j = 0; j < n; ++j) {
            let temp = matrix[i][j];
            matrix[i][j] = matrix[n - i - 1][j];
            matrix[n - i - 1][j] = temp;
        }
    }
    // 主对角线翻转
    for (let i = 0; i < n; ++i) {
        for (let j = 0; j < i; ++j) {
            let temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }
};

```

> 复杂度分析

时间复杂度：O(N ^ 2)。

空间复杂度：O(1)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了27.48%的用户

内存消耗：37.9 MB, 在所有 JavaScript 提交中击败了70.74%的用户
