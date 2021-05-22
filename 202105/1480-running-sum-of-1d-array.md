### 

> 题目 1480. 一维数组的动态和

[链接](https://leetcode-cn.com/problems/running-sum-of-1d-array/)

> 思路

使用额外数组

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var runningSum = function (nums) {
    let arr = [nums[0]]
    for (let i = 1; i < nums.length; i++) {
        arr[i] = arr[i - 1] + nums[i]
    }
    return arr
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了90.92%的用户

内存消耗：39.1 MB, 在所有 JavaScript 提交中击败了27.71%的用户
