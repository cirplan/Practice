### 879. 盈利计划

> 题目

[链接](https://leetcode-cn.com/problems/profitable-schemes/)

> 思路

动态规划？

> 代码

```js
/**
 * @param {number} n
 * @param {number} minProfit
 * @param {number[]} group
 * @param {number[]} profit
 * @return {number}
 */
var profitableSchemes = function (n, minProfit, group, profit) {
    const len = group.length, MOD = 1e9 + 7;
    const dp = new Array(len + 1).fill(0).map(() => new Array(n + 1).fill(0).map(() => new Array(minProfit + 1).fill(0)));
    dp[0][0][0] = 1;
    for (let i = 1; i <= len; i++) {
        const members = group[i - 1], earn = profit[i - 1];
        for (let j = 0; j <= n; j++) {
            for (let k = 0; k <= minProfit; k++) {
                if (j < members) {
                    dp[i][j][k] = dp[i - 1][j][k];
                } else {
                    dp[i][j][k] = (dp[i - 1][j][k] + dp[i - 1][j - members][Math.max(0, k - earn)]) % MOD;
                }
            }
        }
    }
    let sum = 0;
    for (let j = 0; j <= n; j++) {
        sum = (sum + dp[len][j][minProfit]) % MOD;
    }
    return sum;
};
```

> 复杂度分析

时间复杂度：O(len×n×minProfit)，其中 len 为数组 group 的长度。
动态规划需要计算的状态总数是 O(len×n×minProfit)，每个状态的值需要 O(1) 的时间计算。

空间复杂度：O(n×minProfit)。使用空间优化的实现，需要创建 n + 1n+1 行，minProfit+1 列的二维数组 dp。

> 执行

执行用时：288 ms, 在所有 JavaScript 提交中击败了7.69%的用户

内存消耗：76.4 MB, 在所有 JavaScript 提交中击败了7.69%的用户
