### 剑指 Offer 56 - I. 数组中数字出现的次数

> 题目

[链接](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)

> 思路

??

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var singleNumbers = function (nums) {
    let ret = 0;
    for (let n of nums) {
        ret ^= n;
    }
    let div = 1;
    while ((div & ret) == 0) {
        div <<= 1;
    }
    let a = 0;
    let b = 0;
    for (let n of nums) {
        if ((div & n) != 0) {
            a ^= n;
        } else {
            b ^= n;
        }
    }
    return [a, b];
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：112 ms, 在所有 JavaScript 提交中击败了38.62%的用户

内存消耗：40.5 MB, 在所有 JavaScript 提交中击败了60.35%的用户
