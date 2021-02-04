### 剑指 Offer 17. 打印从1到最大的n位数

> 题目

输入数字 n，按顺序打印出从 1 到最大的 n 位十进制数。比如输入 3，则打印出 1、2、3 一直到最大的 3 位数 999。

示例 1:

输入: n = 1
输出: [1,2,3,4,5,6,7,8,9]
 
说明：

用返回一个整数列表来代替打印
n 为正整数

> 思路

最简单是循环直接取，也可以用递归。

> 代码

```js
/**
 * @param {number} n
 * @return {number[]}
 */
var printNumbers = function(n) {
    const max = Math.pow(10, n) - 1;
    const res = [];
    for (let i = 1; i <= max; ++i) {
        res.push(i);
    }
    return res;
};
```

> 复杂度分析

时间复杂度 : O(10 ^ n)。

空间复杂度 : O(n)。

> 执行

执行用时：148 ms, 在所有 JavaScript 提交中击败了17.06%的用户

内存消耗：48.4 MB, 在所有 JavaScript 提交中击败了57.50%的用户