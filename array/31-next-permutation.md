### 31. 下一个排列

> 题目

[链接](https://leetcode-cn.com/problems/next-permutation/)

> 思路

* 从右往左找到第一个 nums[i] < nums[i + 1]
* 在从右到 i，找到第一个 nums[i] < nums[j]
* 交换 nums[i] 和 nums[j]，再使用双指针使 [i + 1, n)反转

> 代码
```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var nextPermutation = function (nums) {
    const len = nums.length
    let i = len - 1
    let j = len - 1

    for (; i >= 0; i--) {
        if (i === len - 1) {
            continue
        } else if (nums[i] < nums[i + 1]) {
            break
        }
    }

    if (i !== -1) {
        for (; j >= 0; j--) {
            if (nums[i] < nums[j]) {
                break
            }
        }
        swap(nums, i, j);
    }
    reverse(nums, i + 1, len - 1);
}

function swap(arr, i, j) {
    const temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}

function reverse(arr, i, j) {
    while (i < j) {
        swap(arr, i, j);
        i++;
        j--;
    }
}
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了99.37%的用户

内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了75.57%的用户
