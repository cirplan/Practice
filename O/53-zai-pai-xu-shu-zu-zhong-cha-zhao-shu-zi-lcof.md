### 剑指 Offer 53 - I. 在排序数组中查找数字 I

> 题目

[链接](https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)

> 思路

本质是查找指定数在数组里出现的下标，使用二分法。

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function (nums, target) {
    return helper(nums, target) - helper(nums, target - 1);
    
    function helper(nums, target) {
        let i = 0;
        let j = nums.length - 1;
        while (i <= j) {
            let m = Math.floor((i + j) / 2);
            if (nums[m] <= target) i = m + 1;
            else j = m - 1;
        }
        return i;
    }
};

```

> 复杂度分析

时间复杂度：O(logN)。

空间复杂度：O(1)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了30.75%的用户

内存消耗：38.9 MB, 在所有 JavaScript 提交中击败了78.11%的用户
