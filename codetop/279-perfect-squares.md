### 279. 完全平方数

> 题目

[链接](https://leetcode-cn.com/problems/perfect-squares/)

> 思路

动态规划，dp[i] = MIN(dp[i], dp[i - j * j] + 1)

> 代码

```js
/**
 * @param {number} n
 * @return {number}
 */
var numSquares = function (n) {
    const dp = [...Array(n + 1)].map(_ => 0); // 数组长度为n+1，值均为0
    for (let i = 1; i <= n; i++) {
        dp[i] = i; // 最坏的情况就是每次+1
        for (let j = 1; i - j * j >= 0; j++) {
            dp[i] = Math.min(dp[i], dp[i - j * j] + 1); // 动态转移方程
        }
    }
    return dp[n];
};
```

> 复杂度分析

时间复杂度：O(n*sqrt(n))，sqrt 为平方根

空间复杂度：O(N)。

> 执行
