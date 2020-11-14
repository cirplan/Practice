### 363. 矩形区域不超过 K 的最大数值和

> 题目

给定一个非空二维矩阵 matrix 和一个整数 k，找到这个矩阵内部不大于 k 的最大矩形和。

示例:
```
输入: matrix = [[1,0,1],[0,-2,3]], k = 2
输出: 2 
解释: 矩形区域 [[0, 1], [-2, 3]] 的数值和是 2，且 2 是不超过 k 的最大数字（k = 2）。
```

说明：

矩阵内的矩形区域面积必须大于 0。
如果行数远大于列数，你将如何解答呢？

> 思路

完全没思路，参考了别人的答案。分别固定左右侧点，计算每一行的和，再叠加。最后计算出最大值。

> 代码

```js
/**
 * @param {number[][]} matrix
 * @param {number} k
 * @return {number}
 */
var maxSumSubmatrix = function (matrix, k) {
    const rows = matrix.length;
    const cols = matrix[0].length;
    let max = Number.NEGATIVE_INFINITY;
    for (let l = 0; l < cols; l++) {
        let rowSum = [];

        for (let r = l; r < cols; r++) {
            for (let i = 0; i < rows; i++) {
                rowSum[i] = (rowSum[i] || 0) + matrix[i][r];
            }

            max = Math.max(max, dpmax(rowSum, k));
        }
    }
    
    return max;
};

function dpmax(arr, k) {
    let max = Number.NEGATIVE_INFINITY;

    for (let l = 0; l < arr.length; l++) {
        let sum = 0;
        
        for (let r = l; r < arr.length; r++) {
            sum += arr[r];
            if (sum > max && sum <= k) max = sum;
        }
    }

    return max;
}
```

> 复杂度分析

时间复杂度 : O(N^3)。

空间复杂度 : O(rows)。

> 执行

执行用时：232 ms, 在所有 JavaScript 提交中击败了70.00%的用户

内存消耗：39.9 MB, 在所有 JavaScript 提交中击败了68.97%的用户


