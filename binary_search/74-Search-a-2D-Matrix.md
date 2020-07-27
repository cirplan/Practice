### 74. 搜索二维矩阵

> 题目

编写一个高效的算法来判断 m x n 矩阵中，是否存在一个目标值。该矩阵具有如下特性：

每行中的整数从左到右按升序排列。
每行的第一个整数大于前一行的最后一个整数。

示例 1:
```
输入:
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 3
输出: true
```

示例 2:
```
输入:
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 13
输出: false
```

> 思路

两个关键词是：已排序，寻找目标值。我们很容易就能联想到二分法，但平常的二分法都是一维数组的，现在二维数组怎么办呢？

很简单，我们把二维的转换成一维就好。因为可以通过N计算出 x 和 y。

> 代码

```js
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var searchMatrix = function (matrix, target) {
    if (!matrix.length || !matrix[0].length) return false;

    let m = matrix.length;
    let n = matrix[0].length;
    const size = m * n;

    let low = 0;
    let height = size;

    while (low <= height) {
        const mid = low + Math.floor((height - low) / 2);
        const _m = Math.floor(mid / n);
        const _n = mid % n;
        if ((_m > m - 1) || (_n > n - 1)) return false;
        const val = matrix[_m][_n];
        
        if (val === target) {
            return true;
        } else if (val > target) {
            height = mid - 1;
        } else {
            low = mid + 1;
        }
    }

    return false;
};
```

> 复杂度分析

二分法，时间复杂度是O(log(mn))。

空间复杂度O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了30.19%的用户。

内存消耗：38.1 MB, 在所有 JavaScript 提交中击败了50.00%的用户。


