### 628. 三个数的最大乘积

> 题目

[链接](https://leetcode-cn.com/problems/maximum-product-of-three-numbers/)

> 思路

排序

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maximumProduct = function (nums) {
    nums.sort((a, b) => a - b);
    const n = nums.length;
    return Math.max(nums[0] * nums[1] * nums[n - 1], nums[n - 1] * nums[n - 2] * nums[n - 3]);
};
```

> 复杂度分析

时间复杂度：O(NlogN)。

空间复杂度：O(logN)。

> 执行

执行用时：152 ms, 在所有 JavaScript 提交中击败了35.70%的用户

内存消耗：41.9 MB, 在所有 JavaScript 提交中击败了55.38%的用户
