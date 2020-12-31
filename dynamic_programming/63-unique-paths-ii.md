### 63. 不同路径 II

> 题目

一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。

现在考虑网格中有障碍物。那么从左上角到右下角将会有多少条不同的路径？

网格中的障碍物和空位置分别用 1 和 0 来表示。

示例 1：
```
输入：obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
输出：2
解释：
3x3 网格的正中间有一个障碍物。
从左上角到右下角一共有 2 条不同的路径：
1. 向右 -> 向右 -> 向下 -> 向下
2. 向下 -> 向下 -> 向右 -> 向右
```

示例 2：
```
输入：obstacleGrid = [[0,1],[0,0]]
输出：1

提示：

m == obstacleGrid.length
n == obstacleGrid[i].length
1 <= m, n <= 100
obstacleGrid[i][j] 为 0 或 1
```

> 思路

f(i, j)的路径树为f(i, j - 1) + f(i - 1, j)。所以用动态规划法。

> 代码

```js
/**
 * @param {number[][]} obstacleGrid
 * @return {number}
 */
var uniquePathsWithObstacles = function (obstacleGrid) {
    const n = obstacleGrid.length;
    const m = obstacleGrid[0].length;
    let f = new Array(m).fill(0);
    f[0] = obstacleGrid[0][0] == 0 ? 1 : 0;

    for (let i = 0; i < n; i++) {
        for (let j = 0; j < m; j++) {
            if (obstacleGrid[i][j] == 1) {
                f[j] = 0;
                continue;
            }
            if (j - 1 >= 0 && obstacleGrid[i][j - 1] == 0) {
                f[j] += f[j - 1];
            }
        }
    }

    return f[m - 1];
};
```

> 复杂度分析


时间复杂度：O(nm)。

空间复杂度：O(m)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了79.32%的用户

内存消耗：38.1 MB, 在所有 JavaScript 提交中击败了83.74%的用户

