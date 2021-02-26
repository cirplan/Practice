### 剑指 Offer 49. 丑数

> 题目

[链接](https://leetcode-cn.com/problems/chou-shu-lcof/)

> 思路

使用动态规划，`dp[i]=min(dp[a]×2,dp[b]×3,dp[c]×5)`

> 代码

```js
/**
 * @param {number} n
 * @return {number}
 */
var nthUglyNumber = function (n) {
    let a = 0, b = 0, c = 0;
    let dp = [];
    dp[0] = 1;
    for (let i = 1; i < n; i++) {
        let n2 = dp[a] * 2, n3 = dp[b] * 3, n5 = dp[c] * 5;
        dp[i] = Math.min(Math.min(n2, n3), n5);
        if (dp[i] == n2) a++;
        if (dp[i] == n3) b++;
        if (dp[i] == n5) c++;
    }
    return dp[n - 1];
}
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了82.60%的用户

内存消耗：41.7 MB, 在所有 JavaScript 提交中击败了25.24%的用户