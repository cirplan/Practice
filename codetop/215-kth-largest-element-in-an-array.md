### 215. 数组中的第K个最大元素

> 题目

[链接](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/)

> 思路

暴力

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findKthLargest = function(nums, k) {
    nums.sort((a, b) => a - b);

    return nums[nums.length - k];
};
```

> 复杂度分析

时间复杂度：O(nlogn)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了80.34%的用户

内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了59.72%的用户
