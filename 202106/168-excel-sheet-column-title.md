### 168. Excel表列名称

> 题目

[链接](https://leetcode-cn.com/problems/excel-sheet-column-title/)

> 思路

26进制，但从1开始

> 代码

```js
/**
 * @param {number} columnNumber
 * @return {string}
 */
var convertToTitle = function (columnNumber) {
    const sb = [];
    while (columnNumber !== 0) {
        columnNumber--;
        sb.push(String.fromCharCode(columnNumber % 26 + 'A'.charCodeAt()));
        columnNumber = Math.floor(columnNumber / 26);
    }
    return sb.reverse().join('');
};
```

> 复杂度分析

时间复杂度：O(log26columnNumber)。columnNumber 转换成 2626 进制的位数。

空间复杂度：O(1)。

> 执行

执行用时：112 ms, 在所有 JavaScript 提交中击败了5.26%的用户

内存消耗：37.6 MB, 在所有 JavaScript 提交中击败了63.53%的用户
