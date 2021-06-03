### 119. 杨辉三角 II

> 题目

[链接](https://leetcode-cn.com/problems/pascals-triangle-ii/)

> 思路

迭代

> 代码

```js
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function (rowIndex) {
    const C = new Array(rowIndex + 1).fill(0);
    for (let i = 0; i <= rowIndex; ++i) {
        C[i] = new Array(i + 1).fill(0);
        C[i][0] = C[i][i] = 1;
        for (let j = 1; j < i; j++) {
            C[i][j] = C[i - 1][j - 1] + C[i - 1][j];
        }
    }
    return C[rowIndex];
};
```

> 复杂度分析

时间复杂度：O(rowIndex ^ 2)。

空间复杂度：O(rowIndex ^ 2)。

> 执行

执行用时：72 ms, 在所有 JavaScript 提交中击败了97.77%的用户

内存消耗：37.8 MB, 在所有 JavaScript 提交中击败了49.68%的用户