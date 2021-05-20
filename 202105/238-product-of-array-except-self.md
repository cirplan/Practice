### 238. 除自身以外数组的乘积

> 题目

[链接](https://leetcode-cn.com/problems/product-of-array-except-self/)

> 思路

？？

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var productExceptSelf = function (nums) {
    const res = [];
    res[0] = 1;
    for (let i = 1; i < nums.length; i++) {
        res[i] = res[i - 1] * nums[i - 1];
    }

    let right = 1;
    for (let j = nums.length - 1; j >= 0; j--) {
        res[j] *= right;
        right *= nums[j];
    }

    return res;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(1)。

> 执行

执行用时：128 ms, 在所有 JavaScript 提交中击败了82.31%的用户

内存消耗：48.4 MB, 在所有 JavaScript 提交中击败了77.39%的用户
