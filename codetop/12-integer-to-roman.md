### 12. 整数转罗马数字

> 题目

[链接](https://leetcode-cn.com/problems/integer-to-roman/)

> 思路
 
暴力适配

> 代码

```js
/**
 * @param {number} num
 * @return {string}
 */
var intToRoman = function (num) {
    var Q = ["", "M", "MM", "MMM"];
    var B = ["", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"];
    var S = ["", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"];
    var G = ["", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"];
    return Q[Math.floor(num / 1000)] + B[Math.floor((num % 1000) / 100)] + S[Math.floor((num % 100) / 10)] + G[num % 10];
};
```

> 复杂度分析

时间复杂度：O(1)。

空间复杂度：O(1)。

> 执行

执行用时：164 ms, 在所有 JavaScript 提交中击败了62.58%的用户

内存消耗：44 MB, 在所有 JavaScript 提交中击败了46.10%的用户
