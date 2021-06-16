### 877. 石子游戏

> 题目

[链接](https://leetcode-cn.com/problems/stone-game/)

> 思路

动态规划

> 代码

```js
/**
 * @param {number[]} piles
 * @return {boolean}
 */
var stoneGame = function (piles) {
    const length = piles.length;
    const dp = new Array(length).fill(0);
    for (let i = 0; i < length; i++) {
        dp[i] = piles[i];
    }
    for (let i = length - 2; i >= 0; i--) {
        for (let j = i + 1; j < length; j++) {
            dp[j] = Math.max(piles[i] - dp[j], piles[j] - dp[j - 1]);
        }
    }
    return dp[length - 1] > 0;
};
```

> 复杂度分析

时间复杂度：O(n ^ 2)。

空间复杂度：O(n)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了87.31%的用户

内存消耗：37.8 MB, 在所有 JavaScript 提交中击败了49.75%的用户
