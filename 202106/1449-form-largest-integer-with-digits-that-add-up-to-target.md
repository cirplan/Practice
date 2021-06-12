### 1449. 数位成本和为目标值的最大数字

> 题目

[链接](https://leetcode-cn.com/problems/form-largest-integer-with-digits-that-add-up-to-target/)

> 思路

??

> 代码

```js
/**
 * @param {number[]} cost
 * @param {number} target
 * @return {string}
 */
var largestNumber = function(cost, target) {
    const dp = new Array(10).fill(0).map(() => new Array(target + 1).fill(-Number.MAX_VALUE));
    const from = new Array(10).fill(0).map(() => new Array(target + 1).fill(0));
    dp[0][0] = 0;
    for (let i = 0; i < 9; ++i) {
        const c = cost[i];
        for (let j = 0; j <= target; ++j) {
            if (j < c) {
                dp[i + 1][j] = dp[i][j];
                from[i + 1][j] = j;
            } else {
                if (dp[i][j] > dp[i + 1][j - c] + 1) {
                    dp[i + 1][j] = dp[i][j];
                    from[i + 1][j] = j;
                } else {
                    dp[i + 1][j] = dp[i + 1][j - c] + 1;
                    from[i + 1][j] = j - c;
                }
            }
        }
    }
    if (dp[9][target] < 0) {
        return "0";
    }
    const sb = [];
    let i = 9, j = target;
    while (i > 0) {
        if (j === from[i][j]) {
            --i;
        } else {
            sb.push(i);
            j = from[i][j];
        }
    }
    return sb.join('');
};

```

> 复杂度分析

时间复杂度：?。

空间复杂度：?。

> 执行

执行用时：112 ms, 在所有 JavaScript 提交中击败了75.00%的用户

内存消耗：44.9 MB, 在所有 JavaScript 提交中击败了37.50%的用户