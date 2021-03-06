### 剑指 Offer 57. 和为s的两个数字

> 题目

[链接](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

> 思路

设置两个指针，分别从起点和终点开始，两值相加。和大于target，则end--；如果和小于target，则start++

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function (nums, target) {
    let start = 0;
    let end = nums.length - 1;

    while (start < end) {
        const res = nums[start] + nums[end];
        if (res === target) {
            return [nums[start], nums[end]];
        } else if (res > target) {
            end--;
        } else {
            start++;
        }
    }
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：116 ms, 在所有 JavaScript 提交中击败了83.64%的用户

内存消耗：53.2 MB, 在所有 JavaScript 提交中击败了55.98%的用户
