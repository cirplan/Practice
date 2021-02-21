### 剑指 Offer 39. 数组中出现次数超过一半的数字

> 题目

[链接](https://leetcode-cn.com/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)

> 思路

循环，当前出现的数字与上一个一致，则计数+1，否则-1，当为），则记录下一个数。到最后剩下的肯定是次数多于长度一半的数。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function (nums) {
    let prevNum = null;
    let prevCount = 0;

    for (let i = 0; i < nums.length; i++) {
        const num = nums[i];

        if (prevNum !== num) {
            prevCount--;

            if (prevCount < 1) {
                prevCount = 1;
                prevNum = num;
            }
        } else {
            prevCount++;
        }
    }

    return prevNum;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：84 ms, 在所有 JavaScript 提交中击败了87.23%的用户

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了93.65%的用户