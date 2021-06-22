### 59. 螺旋矩阵 II

> 题目

[链接](https://leetcode-cn.com/problems/spiral-matrix-ii/)

> 思路

模拟

> 代码

```js
/**
 * @param {number} n
 * @return {number[][]}
 */
var generateMatrix = function (n) {
    let num = 1;
    const matrix = new Array(n).fill(0).map(() => new Array(n).fill(0));
    let left = 0, right = n - 1, top = 0, bottom = n - 1;
    while (left <= right && top <= bottom) {
        for (let column = left; column <= right; column++) {
            matrix[top][column] = num;
            num++;
        }
        for (let row = top + 1; row <= bottom; row++) {
            matrix[row][right] = num;
            num++;
        }
        if (left < right && top < bottom) {
            for (let column = right - 1; column > left; column--) {
                matrix[bottom][column] = num;
                num++;
            }
            for (let row = bottom; row > top; row--) {
                matrix[row][left] = num;
                num++;
            }
        }
        left++;
        right--;
        top++;
        bottom--;
    }
    return matrix;
};
```

> 复杂度分析

时间复杂度：O(n ^ 2)。

空间复杂度：O(1)。

> 执行

执行用时：124 ms, 在所有 JavaScript 提交中击败了6.43%的用户

内存消耗：38.2 MB, 在所有 JavaScript 提交中击败了12.90%的用户
