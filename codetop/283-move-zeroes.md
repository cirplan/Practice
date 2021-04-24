### 283. 移动零

> 题目

[链接](https://leetcode-cn.com/problems/move-zeroes/)

> 思路

双指针

> 代码

```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function (nums) {
    let n = nums.length
    let left = 0
    let right = 0;
    while (right < n) {
        if (nums[right] != 0) {
            swap(nums, left, right);
            left++;
        }
        right++;
    }
}


function swap(nums, left, right) {
    let temp = nums[left];
    nums[left] = nums[right];
    nums[right] = temp;
}
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了93.43%的用户

内存消耗：39.7 MB, 在所有 JavaScript 提交中击败了24.52%的用户