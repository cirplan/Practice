### 剑指 Offer 03. 数组中重复的数字

> 题目

找出数组中重复的数字。

在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

示例 1：

输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 
 
限制：

2 <= n <= 100000

> 思路

直接用set或map记录出现的数字，再判断即可。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findRepeatNumber = function (nums) {
    let cache = new Set();
    for (let i = 0; i < nums.length; i++) {
        const num = nums[i];
        if (cache.has(num)) {
            return num;
        } else {
            cache.add(num);
        }
    }
};
```

> 复杂度分析

时间复杂度 : O(n)。

空间复杂度 : O(n)。

> 执行

执行用时：100 ms, 在所有 JavaScript 提交中击败了60.22%的用户

内存消耗：45.8 MB, 在所有 JavaScript 提交中击败了18.54%的用户
