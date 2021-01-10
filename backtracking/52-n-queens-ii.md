### 52. N皇后 II

> 题目

n 皇后问题 研究的是如何将 n 个皇后放置在 n×n 的棋盘上，并且使皇后彼此之间不能相互攻击。

给你一个整数 n ，返回 n 皇后问题 不同的解决方案的数量。

示例 1：
```
输入：n = 4
输出：2
解释：如上图所示，4 皇后问题存在两个不同的解法。
```

示例 2：
```
输入：n = 1
输出：1
```

提示：

1 <= n <= 9
皇后彼此不能相互攻击，也就是说：任何两个皇后都不能处于同一条横行、纵行或斜线上。

> 思路

?

> 代码

```js
/**
 * @param {number} n
 * @return {number}
 */
var totalNQueens = function (n) {
    const board = new Array(n);
    for (let i = 0; i < n; i++) {
        board[i] = new Array(n).fill('.');
    }

    const cols = new Set();
    const diag1 = new Set();
    const diag2 = new Set();
    let res = 0;

    const helper = (row) => {
        if (row == n) {
            const stringsBoard = board.slice();
            for (let i = 0; i < n; i++) {
                stringsBoard[i] = stringsBoard[i].join('');
            }
            res++;
            return;
        }
        for (let col = 0; col < n; col++) {
            if (!cols.has(col) && !diag1.has(row + col) && !diag2.has(row - col)) {
                board[row][col] = 'Q';
                cols.add(col);
                diag1.add(row + col);
                diag2.add(row - col);
                helper(row + 1);
                board[row][col] = '.';
                cols.delete(col);
                diag1.delete(row + col);
                diag2.delete(row - col);
            }
        }
    };
    helper(0);
    return res;
};
```

> 复杂度分析

时间复杂度：?。

空间复杂度：?。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了69.35%的用户

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了36.93%的用户