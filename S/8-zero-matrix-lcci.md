### 面试题 01.08. 零矩阵

> 题目

[链接](https://leetcode-cn.com/problems/zero-matrix-lcci/)

> 思路

使用两个数组分别记录行和列为0的，再循环赋值。

> 代码

```js
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var setZeroes = function (matrix) {
    const rowLen = matrix.length;
    const colLen = matrix[0].length;
    let zeroRow = new Array(rowLen);
    let zeroCol = new Array(colLen);

    for (let i = 0; i < rowLen; i++) {
        for (let j = 0; j < colLen; j++) {
            const num = matrix[i][j];
            if (num === 0) {
                zeroRow[i] = 1;
                zeroCol[j] = 1;
            }
        }
    }
    
    for (let i = 0; i < rowLen; i++) {
        if (zeroRow[i] === 1) {
            for (let j = 0; j < colLen; j++) {
                matrix[i][j] = 0;
            }
        }
    }

    for (let j = 0; j < colLen; j++) {
        if (zeroCol[j] === 1) {
            for (let i = 0; i < rowLen; i++) {
                matrix[i][j] = 0;
            }
        }
    }
};
```

> 复杂度分析

时间复杂度：O(NM)。

空间复杂度：O(N)。N 为 N，M 中最大值

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了86.46%的用户

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了92.27%的用户
