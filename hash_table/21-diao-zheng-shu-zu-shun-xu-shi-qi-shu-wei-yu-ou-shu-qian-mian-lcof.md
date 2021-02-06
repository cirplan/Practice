### 剑指 Offer 21. 调整数组顺序使奇数位于偶数前面

> 题目

[链接](https://leetcode-cn.com/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

> 思路

使用快慢指针，左指针往右找偶数，右指针往左找奇数，然后交换。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var exchange = function (nums) {
    let start = 0;
    let end = nums.length - 1;

    while (start < end) {
        while (isOdd(nums[start]) && start < end) {
            start++;
        }
        while (!isOdd(nums[end]) && start < end) {
            end--;
        }
        if (start < end) {
            let temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
        }
    }

    return nums;
};

function isOdd(num) {
    return num % 2 !== 0;
}
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：108 ms, 在所有 JavaScript 提交中击败了92.80%的用户

内存消耗：45.1 MB, 在所有 JavaScript 提交中击败了81.15%的用户
