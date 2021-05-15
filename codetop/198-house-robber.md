### 198. 打家劫舍

> 题目

[链接](https://leetcode-cn.com/problems/house-robber/)

> 思路

使用动态规划

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function (nums) {
    const len = nums.length;
    if (len == 0)
        return 0;
    const dp = new Array(len + 1);
    dp[0] = 0;
    dp[1] = nums[0];
    for (let i = 2; i <= len; i++) {
        dp[i] = Math.max(dp[i - 1], dp[i - 2] + nums[i - 1]);
    }
    return dp[len];
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(n)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了41.01%的用户

内存消耗：37.5 MB, 在所有 JavaScript 提交中击败了91.44%的用户
