### 268. 丢失的数字

> 题目

[链接](https://leetcode-cn.com/problems/missing-number/)

> 思路

数学方法

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var missingNumber = function (nums) {
    let sum = 0;
    for (let i = 1; i <= nums.length; i++) {
        sum += i;
        sum -= nums[i - 1];
    }
    return sum;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：60 ms, 在所有 JavaScript 提交中击败了100.00%的用户

内存消耗：39.9 MB, 在所有 JavaScript 提交中击败了91.87%的用户
