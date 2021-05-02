### 55. 跳跃游戏    

> 题目

[链接](https://leetcode-cn.com/problems/jump-game/)

> 思路

维持最大可达位置

> 代码

```js
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var canJump = function (nums) {
    let n = nums.length;
    let rightmost = 0;
    for (let i = 0; i < n; ++i) {
        if (i <= rightmost) {
            rightmost = Math.max(rightmost, i + nums[i]);
            if (rightmost >= n - 1) {
                return true;
            }
        }
    }
    return false;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了96.42%的用户

内存消耗：38.3 MB, 在所有 JavaScript 提交中击败了97.64%的用户
