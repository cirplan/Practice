### 27. 移除元素

> 题目

[链接](https://leetcode-cn.com/problems/remove-element/)

> 思路

使用双指针

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */
var removeElement = function(nums, val) {
    const len = nums.length;
    if (!len) return 0;
    let i = 0;
    let j = len - 1;
    while (i <= j) {
        if (nums[i] === val) {
            let temp = nums[i];
            nums[i] = nums[j];
            nums[j] = temp;
            j--;
        } else {
            i++;
        }
    }

    return j + 1;
};

```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了31.02%的用户

内存消耗：37.8 MB, 在所有 JavaScript 提交中击败了81.43%的用户
