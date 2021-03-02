### 剑指 Offer 53 - II. 0～n-1中缺失的数字

> 题目

[链接](https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof/)

> 思路

使用二分法，找到第一个num[i] != i的元素。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var missingNumber = function (nums) {
    let i = 0;
    let j = nums.length - 1;
    while (i <= j) {
        let m = Math.floor((i + j) / 2);
        if (nums[m] == m) i = m + 1;
        else j = m - 1;
    }
    return i;
};
```

> 复杂度分析

时间复杂度：O(logN)。

空间复杂度：O(1)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了27.51%的用户

内存消耗：40 MB, 在所有 JavaScript 提交中击败了71.88%的用户
