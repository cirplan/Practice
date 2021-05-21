### 79. 单词搜索

> 题目

[链接](https://leetcode-cn.com/problems/word-search/)

> 思路

??

> 代码

```js
/**
 * @param {character[][]} board
 * @param {string} word
 * @return {boolean}
 */
var exist = function (board, word) {
    const h = board.length, w = board[0].length;
    const directions = [[0, 1], [0, -1], [1, 0], [-1, 0]];
    const visited = new Array(h);
    for (let i = 0; i < visited.length; ++i) {
        visited[i] = new Array(w).fill(false);
    }
    const check = (i, j, s, k) => {
        if (board[i][j] != s.charAt(k)) {
            return false;
        } else if (k == s.length - 1) {
            return true;
        }
        visited[i][j] = true;
        let result = false;
        for (const [dx, dy] of directions) {
            let newi = i + dx, newj = j + dy;
            if (newi >= 0 && newi < h && newj >= 0 && newj < w) {
                if (!visited[newi][newj]) {
                    const flag = check(newi, newj, s, k + 1);
                    if (flag) {
                        result = true;
                        break;
                    }
                }
            }
        }
        visited[i][j] = false;
        return result;
    }

    for (let i = 0; i < h; i++) {
        for (let j = 0; j < w; j++) {
            const flag = check(i, j, word, 0);
            if (flag) {
                return true;
            }
        }
    }
    return false;
};
```

> 复杂度分析

时间复杂度： O(MN * 3^L)。

空间复杂度：O(MN)。

> 执行

执行用时：388 ms, 在所有 JavaScript 提交中击败了26.99%的用户

内存消耗：40 MB, 在所有 JavaScript 提交中击败了67.10%的用户
