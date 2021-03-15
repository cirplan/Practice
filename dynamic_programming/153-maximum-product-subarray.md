### 152. 乘积最大子数组

> 题目

[链接](https://leetcode-cn.com/problems/maximum-product-subarray/)

> 思路

分别维护最大，最小的值。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxProduct = function (nums) {
    let res = nums[0]
    let prevMin = nums[0]
    let prevMax = nums[0]
    let temp1 = 0, temp2 = 0
    for (let i = 1; i < nums.length; i++) {
        temp1 = prevMin * nums[i]
        temp2 = prevMax * nums[i]
        prevMin = Math.min(temp1, temp2, nums[i])
        prevMax = Math.max(temp1, temp2, nums[i])
        res = Math.max(prevMax, res)
    }
    return res
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了74.42%的用户

内存消耗：39.1 MB, 在所有 JavaScript 提交中击败了88.22%的用户
