### 剑指 Offer 65. 不用加减乘除做加法

> 题目

[链接](https://leetcode-cn.com/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/)

> 思路

??

> 代码

```js
/**
 * @param {number} a
 * @param {number} b
 * @return {number}
 */
var add = function (a, b) {
    while (b != 0) { // 当进位为 0 时跳出
        let c = (a & b) << 1;  // c = 进位
        a ^= b; // a = 非进位和
        b = c; // b = 进位
    }
    return a;
};
```

> 复杂度分析

时间复杂度：O(1)。

空间复杂度：O(1)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了66.53%的用户

内存消耗：37.7 MB, 在所有 JavaScript 提交中击败了24.84%的用户