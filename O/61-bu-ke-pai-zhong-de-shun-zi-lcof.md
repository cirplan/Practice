### 剑指 Offer 61. 扑克牌中的顺子

> 题目

[链接](https://leetcode-cn.com/problems/bu-ke-pai-zhong-de-shun-zi-lcof/)

> 思路

找出为0的个数，还有间隔的数量。当为0的个数大于等于间隔数，即可。

> 代码

```js
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var isStraight = function (nums) {
    nums = nums.sort((a, b) => a - b);

    let zeroCount = 0;
    let stepCount = 0;
    let prevNum;
    for (let i = 0; i < 5; i++) {
        const num = nums[i];
        if (num === 0) {
            zeroCount++;
        } else {
            if (prevNum) {
                if (prevNum === num) {
                    return false;
                }
                stepCount += num - prevNum - 1;
            }

            prevNum = num;
        }
    }

    if (zeroCount >= stepCount) {
        return true;
    }

    return false;
};
```

> 复杂度分析

时间复杂度：O(nlogn)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了50.39%的用户

内存消耗：38.9 MB, 在所有 JavaScript 提交中击败了55.13%的用户