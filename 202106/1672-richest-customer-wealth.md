### 1672. 最富有客户的资产总量

> 题目

[链接](https://leetcode-cn.com/problems/richest-customer-wealth/)

> 思路

循环

> 代码

```js
/**
 * @param {number[][]} accounts
 * @return {number}
 */
var maximumWealth = function (accounts) {
    return accounts.reduce((max, account) => Math.max(max, account.reduce((pre, cur) => pre + cur, 0)), 0);
};
```

> 复杂度分析

时间复杂度：O(N ^ 2)。

空间复杂度：O(1)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了33.27%的用户

内存消耗：38.1 MB, 在所有 JavaScript 提交中击败了76.81%的用户
