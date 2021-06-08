### 1049. 最后一块石头的重量 II

> 题目

[链接](https://leetcode-cn.com/problems/last-stone-weight-ii/)

> 思路

动态规划？

> 代码

```js
/**
 * @param {number[]} stones
 * @return {number}
 */
var lastStoneWeightII = function (stones) {
    let sum = 0;
    for (const weight of stones) {
        sum += weight;
    }
    const m = Math.floor(sum / 2);
    const dp = new Array(m + 1).fill(false);
    dp[0] = true;
    for (const weight of stones) {
        for (let j = m; j >= weight; --j) {
            dp[j] = dp[j] || dp[j - weight];
        }
    }
    for (let j = m; ; --j) {
        if (dp[j]) {
            return sum - 2 * j;
        }
    }
};
```

> 复杂度分析

时间复杂度：O(n⋅sum)。

空间复杂度：O(sum)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了84.27%的用户

内存消耗：38.9 MB, 在所有 JavaScript 提交中击败了39.33%的用户
