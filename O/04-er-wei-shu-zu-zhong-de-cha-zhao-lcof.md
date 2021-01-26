### 剑指 Offer 04. 二维数组中的查找

> 题目

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

示例:
```
现有矩阵 matrix 如下：

[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。

给定 target = 20，返回 false。
```
 
限制：

0 <= n <= 1000

0 <= m <= 1000

> 思路

可以用暴力破解。但更巧妙是线性判断，取右上角的数，如果等于target直接返回。当大于target，则消除当前列。若小于target，则消除当前行。

> 代码

```js
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var findNumberIn2DArray = function (matrix, target) {
    if (!matrix.length) {
        return false;
    }
    let n = matrix.length;
    let m = matrix[0].length;
    let _n = 0;
    let _m = m - 1;
    while (_n < n && _m >= 0) {
        const num = matrix[_n][_m];
        if (num === target) {
            return true;
        } else if (num > target) {
            _m--;
        } else {
            _n++;
        }
    }

    return false;
};
```

> 复杂度分析

时间复杂度 : O(n+m)。

空间复杂度 : O(1)。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了96.97%的用户

内存消耗：41.2 MB, 在所有 JavaScript 提交中击败了18.42%的用户