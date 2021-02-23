### 剑指 Offer 42. 连续子数组的最大和

> 题目

[链接](https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

> 思路

 对数组循环，取元素值累加。从前往后，当和小于等于0，则和为当前值。否则和加上当前值。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function (nums) {
    let max = -Infinity;
    let sum = 0;
    for (let i = 0; i < nums.length; i++) {
        const num = nums[i];
        if (sum <= 0) {
            sum = num;
        } else {
            sum += num;
        }

        if (sum > max) {
            max = sum;
        }
    }

    return max;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了70.19%的用户

内存消耗：41.4 MB, 在所有 JavaScript 提交中击败了63.66%的用户