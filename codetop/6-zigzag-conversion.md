### 6. Z 字形变换

> 题目

[链接](https://leetcode-cn.com/problems/zigzag-conversion/)

> 思路

使用对应数组，关键在于迭代方向控制

> 代码

```js
/**
 * @param {string} s
 * @param {number} numRows
 * @return {string}
 */
var convert = function (s, numRows) {
    if (numRows == 1)
        return s;

    const len = Math.min(s.length, numRows);
    const rows = [];
    for (let i = 0; i < len; i++) rows[i] = "";
    let loc = 0;
    let down = false;

    for (const c of s) {
        rows[loc] += c;
        if (loc == 0 || loc == numRows - 1)
            down = !down;
        loc += down ? 1 : -1;
    }

    let ans = "";
    for (const row of rows) {
        ans += row;
    }
    return ans;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：120 ms, 在所有 JavaScript 提交中击败了55.71%的用户

内存消耗：42.1 MB, 在所有 JavaScript 提交中击败了57.31%的用户
