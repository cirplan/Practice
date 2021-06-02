### 485. 最大连续 1 的个数

> 题目

[链接](https://leetcode-cn.com/problems/max-consecutive-ones/)

> 思路

遍历

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function (nums) {
    let maxCount = 0, count = 0;
    const n = nums.length;
    for (let i = 0; i < n; i++) {
        if (nums[i] === 1) {
            count++;
        } else {
            maxCount = Math.max(maxCount, count);
            count = 0;
        }
    }
    maxCount = Math.max(maxCount, count);
    return maxCount;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(1)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了59.58%的用户

内存消耗：40.2 MB, 在所有 JavaScript 提交中击败了84.19%的用户