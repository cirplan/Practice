### 518. 零钱兑换 II

> 题目

[链接](https://leetcode-cn.com/problems/coin-change-2/)

> 思路

动态规划

> 代码

```js
/**
 * @param {number} amount
 * @param {number[]} coins
 * @return {number}
 */
var change = function (amount, coins) {
    const dp = new Array(amount + 1).fill(0);
    dp[0] = 1;
    for (const coin of coins) {
        for (let i = coin; i <= amount; i++) {
            dp[i] += dp[i - coin];
        }
    }
    return dp[amount];
};
```

> 复杂度分析

时间复杂度：O(amount * n)。

空间复杂度：O(amount)。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了41.52%的用户

内存消耗：38.4 MB, 在所有 JavaScript 提交中击败了62.38%的用户
