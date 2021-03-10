### 剑指 Offer 59 - I. 滑动窗口的最大值

> 题目

[链接](https://leetcode-cn.com/problems/hua-dong-chuang-kou-de-zui-da-zhi-lcof/)

> 思路

可以使用暴力破解，但更巧妙的是使用一个队列。

* 若 i > 0 且 队首元素 deque[0] == 被删除元素 nums[i - 1]：则队首元素出队；
* 删除 deque 内所有 < nums[j] 的元素，以保持 deque 递减；
* 将 nums[j] 添加至 deque 尾部
* 若已形成窗口（即 i≥0 ）：将窗口最大值（即队首元素 deque[0] ）添加至列表 res


> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var maxSlidingWindow = function (nums, k) {
    if (!nums.length) return [];
    let deque = [];
    let i = 0;
    let res = [];
    const len = nums.length;
    // 未形成窗口
    for (let i = 0; i < k; i++) {
        while (deque.length && deque[deque.length - 1] < nums[i]) {
            deque.pop();
        }
        deque.push(nums[i]);
    }

    res[0] = deque[0];
    // 形成窗口后
    for (let i = k; i < nums.length; i++) {
        if (deque[0] == nums[i - k]) {
            deque.shift();
        }
        while (deque.length && deque[deque.length - 1] < nums[i]) {
            deque.pop();
        }

        deque.push(nums[i]);
        res[i - k + 1] = deque[0];
    }
    return res;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(k)。

> 执行

执行用时：112 ms, 在所有 JavaScript 提交中击败了85.57%的用户

内存消耗：43.9 MB, 在所有 JavaScript 提交中击败了69.73%的用户
