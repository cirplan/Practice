### 287. 寻找重复数

> 题目

[链接](https://leetcode-cn.com/problems/find-the-duplicate-number/)

> 思路

使用快慢指针

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findDuplicate = function (nums) {
    let slow = 0, fast = 0;
    do {
        slow = nums[slow];
        fast = nums[nums[fast]];
    } while (slow != fast);
    slow = 0;
    while (slow != fast) {
        slow = nums[slow];
        fast = nums[fast];
    }
    return slow;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：128 ms, 在所有 JavaScript 提交中击败了20.25%的用户

内存消耗：46.3 MB, 在所有 JavaScript 提交中击败了15.17%的用户
