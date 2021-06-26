### 909. 蛇梯棋

> 题目

[链接](https://leetcode-cn.com/problems/snakes-and-ladders/)

> 思路

广度优先

> 代码

```js
/**
 * @param {number[][]} board
 * @return {number}
 */
var snakesAndLadders = function (board) {
    const n = board.length;
    const vis = new Array(n * n + 1).fill(0);
    const queue = [[1, 0]];
    while (queue.length) {
        const p = queue.shift();
        for (let i = 1; i <= 6; ++i) {
            let nxt = p[0] + i;
            if (nxt > n * n) { // 超出边界
                break;
            }
            const rc = id2rc(nxt, n); // 得到下一步的行列
            if (board[rc[0]][rc[1]] > 0) { // 存在蛇或梯子
                nxt = board[rc[0]][rc[1]];
            }
            if (nxt === n * n) { // 到达终点
                return p[1] + 1;
            }
            if (!vis[nxt]) {
                vis[nxt] = true;
                queue.push([nxt, p[1] + 1]); // 扩展新状态
            }
        }
    }
    return -1;
};

const id2rc = (id, n) => {
    let r = Math.floor((id - 1) / n), c = (id - 1) % n;
    if (r % 2 === 1) {
        c = n - 1 - c;
    }
    return [n - 1 - r, c];
}
```

> 复杂度分析

时间复杂度：O(N ^ 2)。

空间复杂度：O(N ^ 2)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了100.00%的用户

内存消耗：40.5 MB, 在所有 JavaScript 提交中击败了50.00%的用户
